# Get All Orders (USDⓈ-M Futures)

Retrieves all orders; active, canceled, or filled, for a specific symbol on the USDⓈ-M Futures market.

## Endpoint

*   **`GET /fapi/v1/allOrders`** (Verify endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`USER_DATA`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Futures documentation)*

*   **`symbol`** (Mandatory): The symbol to get orders for (e.g., `BTCUSDT`).
*   **`orderId`** (Optional): If set, it will get orders >= `orderId`. Otherwise, the most recent orders are returned.
*   **`startTime`** (Optional): Timestamp in ms to get orders from INCLUSIVE.
*   **`endTime`** (Optional): Timestamp in ms to get orders until INCLUSIVE.
*   **`limit`** (Optional): Default 500; max 1000.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Returns an array of order detail objects.

*(Conceptual structure - array of objects similar to the Query Order response)*

```json
// Example Response (Conceptual - Array of orders)
[
  {
    "orderId": 2831942115,
    "symbol": "BTCUSDT",
    "status": "FILLED", 
    "clientOrderId": "myOrder1", 
    "price": "9000",
    "avgPrice": "9001.50",
    "origQty": "0.001",
    "executedQty": "0.001",
    "cumQuote": "9.0015",
    "timeInForce": "GTC",
    "type": "LIMIT",
    "reduceOnly": false,
    "closePosition": false,
    "side": "BUY",
    "positionSide": "BOTH",
    "stopPrice": "0", 
    "workingType": "CONTRACT_PRICE",
    "priceProtect": false,
    "origType": "LIMIT",
    "time": 1578966608735, 
    "updateTime": 1578966609500 
  },
  {
    "orderId": 2831942116,
    "symbol": "BTCUSDT",
    "status": "CANCELED",
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
    "updateTime": 1578966615000 
  },
  // ... other orders matching criteria
]
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   If `startTime` and `endTime` are both not sent, the last 7 days' data will be returned.
*   The maximum time range between `startTime` and `endTime` is 7 days.
*   Be aware that very old (`created time + 30 days < current time`) canceled or expired orders with no fills might be pruned and not returned by this endpoint (See Change Log 2020-05-18). 