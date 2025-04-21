# Get Current Open Orders (Spot)

Retrieves all currently open orders on the Spot market for the account.

## Endpoint

*   **`GET /api/v3/openOrders`** (Verify exact endpoint in official Spot API docs)

## Base URLs

*   `https://api.binance.com` (Primary)
*   `https://api1.binance.com`
*   `https://api2.binance.com`
*   `https://api3.binance.com`
*   `https://api4.binance.com`

## Security Type

*   **`USER_DATA`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Spot documentation)*

*   **`symbol`** (Optional): If provided, only open orders for this symbol are returned.
*   **`recvWindow`** (Optional): The time window (in milliseconds) during which the request is valid (max typically 60000ms).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature of all parameters.

## Response Payload

Returns an array of order detail objects for all open orders.

*(Conceptual structure - likely an array of objects similar to the Query Order response)*

```json
// Example Response (Conceptual)
[
  {
    "symbol": "BTCUSDT",
    "orderId": 29,
    "orderListId": -1,
    "clientOrderId": "myOpenOrder1",
    "price": "58000.00",
    "origQty": "0.1",
    "executedQty": "0.0",
    "cummulativeQuoteQty": "0.0",
    "status": "NEW",
    "timeInForce": "GTC",
    "type": "LIMIT",
    "side": "BUY",
    "stopPrice": "0.0",
    "icebergQty": "0.0",
    "time": 1619888400000,
    "updateTime": 1619888400000,
    "isWorking": true,
    "origQuoteOrderQty": "0.0"
  },
  // ... other open orders ...
]
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   If no `symbol` is sent, open orders for **all symbols** are returned. Be mindful of potential response size. 