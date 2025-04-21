# Get Current Open Orders (USDⓈ-M Futures)

Retrieves all currently open orders on the USDⓈ-M Futures market for the account.

## Endpoint

*   **`GET /fapi/v1/openOrders`**
*   *Also `GET /fapi/v1/openOrder` for a single open order (see change log 2020-02-20)*

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`USER_DATA`** (Requires API Key and Signature)

## Parameters (`/openOrders`)

*(Note: Verify exact mandatory/optional parameters in official Futures documentation)*

*   **`symbol`** (Optional): If provided, only open orders for this symbol are returned.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Parameters (`/openOrder` - Query Single Order)

*   **`symbol`** (Mandatory)
*   **`orderId`** (Optional)
*   **`origClientOrderId`** (Optional)
*   **`recvWindow`** (Optional)
*   **`timestamp`** (Mandatory)
*   **`signature`** (Mandatory)
*   *(At least one of `orderId` or `origClientOrderId` must be sent)*

## Response Payload (`/openOrders`)

Returns an array of order detail objects for all open orders.

*(Conceptual structure - likely an array of objects similar to the Query Order response)*

```json
// Example Response (Conceptual)
[
  {
    "orderId": 2831942116,
    "symbol": "BTCUSDT",
    "status": "NEW",
    "clientOrderId": "myOpenOrder2",
    "price": "9100",
    "avgPrice": "0.00000",
    "origQty": "0.002",
    "executedQty": "0",
    "cumQuote": "0",
    "timeInForce": "GTC",
    "type": "LIMIT",
    "reduceOnly": false,
    "closePosition": false,
    "side": "SELL",
    "positionSide": "BOTH",
    "stopPrice": "0", 
    "workingType": "CONTRACT_PRICE",
    "priceProtect": false,
    "origType": "LIMIT",
    "time": 1578966610000,
    "updateTime": 1578966610000 
  },
  // ... other open orders ...
]
```

## Response Payload (`/openOrder`)

Returns a single order detail object if found and open.

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   `/openOrders`: If no `symbol` is sent, open orders for **all symbols** are returned. Be mindful of potential response size. 