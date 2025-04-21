# Cancel Order (USDⓈ-M Futures)

Cancels an active order on the USDⓈ-M Futures market.

## Endpoint

*   **`DELETE /fapi/v1/order`** (Verify endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`TRADE`** (Requires API Key and Signature)

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

Successful cancellation returns details of the cancelled order.

*(Conceptual structure - likely similar to Place Order ACK response)*

```json
// Example Response (Conceptual)
{
    "orderId": 2831942115,
    "symbol": "BTCUSDT",
    "status": "CANCELED",
    "clientOrderId": "myOrder1", // origClientOrderId or clientOrderId that was cancelled
    "price": "9000",
    "avgPrice": "0.00000",
    "origQty": "0.001",
    "executedQty": "0",
    "cumQuote": "0",
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
    "updateTime": 1578966608735 
}
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   An order can only be cancelled if its status is still active (e.g., `NEW`, `PARTIALLY_FILLED`). 