# Query Order (USDⓈ-M Futures)

Checks the status of a specific order on the USDⓈ-M Futures market.

## Endpoint

*   **`GET /fapi/v1/order`** (Verify endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`USER_DATA`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Futures documentation)*

*   **`symbol`** (Mandatory): The symbol the order was placed for (e.g., `BTCUSDT`).
*   **`orderId`** (Optional): The unique `orderId` assigned by Binance.
*   **`origClientOrderId`** (Optional): The `clientOrderId` assigned by the client when the order was placed.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

**Note:** At least one of `orderId` or `origClientOrderId` must be sent.

## Response Payload

Returns details of the specific order.

*(Conceptual structure - likely similar to Place Order ACK response)*

```json
// Example Response (Conceptual - Filled)
{
    "orderId": 2831942115,
    "symbol": "BTCUSDT",
    "status": "FILLED", 
    "clientOrderId": "myOrder1", 
    "price": "9000",
    "avgPrice": "9001.50", // Average fill price
    "origQty": "0.001",
    "executedQty": "0.001",
    "cumQuote": "9.0015", // Cumulative quote asset transacted
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
    "time": 1578966608735, // Order creation time
    "updateTime": 1578966609500 // Last update time
}
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   This endpoint is used to check the current status of a single order. 