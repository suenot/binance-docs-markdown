# Binance API Authentication

Binance API uses API Keys to authenticate requests for private endpoints (e.g., trading, account management). Public endpoints (e.g., market data) generally do not require authentication.

## Security Types

Endpoints have different security requirements:

*   **`NONE`**: Publicly accessible endpoints.
*   **`TRADE`**: Requires API Key and Signature. Used for placing/managing orders.
*   **`MARGIN`**: Requires API Key and Signature. Used for margin account actions.
*   **`USER_DATA`**: Requires API Key and Signature. Used for accessing private account and user stream data.
*   **`USER_STREAM`**: Requires API Key. Used for managing user data streams (WebSocket).
*   **`MARKET_DATA`**: Requires API Key. Used for accessing certain market data streams.

*(Note: This list might not be exhaustive; always refer to the specific endpoint documentation.)*

## API Key

*   Generated via your Binance account settings.
*   Consists of an **API Key** (public identifier) and a **Secret Key** (private credential).
*   **Never share your Secret Key.**
*   Configure permissions (Read, Trade, Withdrawals) and IP restrictions for security.

## Signed (HMAC SHA256) Endpoints

Endpoints requiring `TRADE`, `MARGIN`, or `USER_DATA` security must include a valid signature in the request.

### Signature Generation

1.  **Create Parameter String:** Concatenate all request parameters (both query string and request body, if applicable) into a single string, ordered alphabetically by parameter name. Example: `param1=value1&param2=value2&timestamp=...`
2.  **Generate HMAC SHA256:** Use your **Secret Key** to create an HMAC SHA256 hash of the parameter string from step 1.
3.  **Append Signature:** Add the resulting hexadecimal hash as a `signature` parameter to your request (either in the query string or request body).

### Passing Parameters

*   For `GET`, `DELETE` requests, all parameters must be in the **query string**.
*   For `POST`, `PUT` requests, parameters can be:
    *   Entirely in the **query string**.
    *   Entirely in the **request body** (with `Content-Type: application/x-www-form-urlencoded`).
    *   Mixed between query string and request body.
*   **Important:** The `signature` must be calculated based on the **total combined** parameters (query string + request body).
*   If a parameter exists in both the query string and request body, the **query string value takes precedence**.

### Timestamp Requirement

*   Signed requests **must** include a `timestamp` parameter.
*   The timestamp should be the **milliseconds** since the UNIX epoch (e.g., `1591702613943`).
*   The request must reach the Binance server within a specific time window (defined by `recvWindow`).

### `recvWindow` Parameter

*   Optional parameter specifying the time window (in milliseconds) during which the request is valid.
*   Default and maximum values vary by API type (e.g., 5000ms for Futures, check specific API docs).
*   If `timestamp` is outside `serverTime +/- recvWindow`, the request is rejected.
*   If the server receives a timestamp more than 1 second *ahead* of its own time, the request is also rejected.

### Request Headers

*   The **API Key** must be sent in the `X-MBX-APIKEY` HTTP header.

### Example (Conceptual - COIN-M Futures)

```
# Parameters (before signing)
symbol=BTCUSD_200925
side=BUY
type=LIMIT
quantity=1
price=9000
timeInForce=GTC
recvWindow=5000
timestamp=1591702613943

# Parameter String (alphabetical order)
price=9000&quantity=1&recvWindow=5000&side=BUY&symbol=BTCUSD_200925&timeInForce=GTC&timestamp=1591702613943&type=LIMIT

# Assume Secret Key is "MySecretKey"
# Calculate HMAC SHA256(parameter_string, MySecretKey)
# Resulting signature (example): 21fd819734bf0e5c68740eed892909414d693635c5f7fffab1313925ae13556a

# Example Curl (POST with parameters in query string)
curl -H "X-MBX-APIKEY: YourApiKey" -X POST \
'https://dapi.binance.com/dapi/v1/order?symbol=BTCUSD_200925&side=BUY&type=LIMIT&quantity=1&price=9000&timeInForce=GTC&recvWindow=5000&timestamp=1591702613943&signature=21fd819734bf0e5c68740eed892909414d693635c5f7fffab1313925ae13556a'

# Example Curl (POST with parameters in request body)
curl -H "X-MBX-APIKEY: YourApiKey" -X POST 'https://dapi.binance.com/dapi/v1/order' \
-d 'symbol=BTCUSD_200925&side=BUY&type=LIMIT&quantity=1&price=9000&timeInForce=GTC&recvWindow=5000&timestamp=1591702613943&signature=21fd819734bf0e5c68740eed892909414d693635c5f7fffab1313925ae13556a'
``` 