# Cancel Order (Spot)

This endpoint cancels an active order on the Spot market.

## Endpoint

*   **`DELETE /api/v3/order`** (Verify exact endpoint in official Spot API docs)

## Base URLs

*   `https://api.binance.com` (Primary)
*   `https://api1.binance.com`
*   `https://api2.binance.com`
*   `https://api3.binance.com`
*   `https://api4.binance.com`

## Security Type

*   **`TRADE`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Spot documentation)*

*   **`symbol`** (Mandatory): The symbol the order was placed for (e.g., `BTCUSDT`).
*   **`orderId`** (Optional): The unique `orderId` assigned by Binance.
*   **`origClientOrderId`** (Optional): The `clientOrderId` assigned by the client when the order was placed.
*   **`newClientOrderId`** (Optional): Used to uniquely identify this cancel request.
*   **`recvWindow`** (Optional): The time window (in milliseconds) during which the request is valid (max typically 60000ms).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature of all parameters.

**Note:** At least one of `orderId` or `origClientOrderId` must be sent.

## Response Payload

Successful cancellation returns details of the cancelled order.

*(Conceptual structure - check official docs)*

```json
// Example Response
{
  "symbol": "BTCUSDT",
  "origClientOrderId": "6gCrw2kRUAF9CvJDGP16IP",
  "orderId": 28,
  "orderListId": -1, // OCO order ID, -1 otherwise
  "clientOrderId": "cancelMyOrder1", // The newClientOrderId sent in the request
  "price": "0.00001000",
  "origQty": "10.00000000",
  "executedQty": "0.00000000",
  "cummulativeQuoteQty": "0.00000000",
  "status": "CANCELED",
  "timeInForce": "GTC",
  "type": "LIMIT",
  "side": "BUY"
}
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   An order can only be cancelled if its status is still active (e.g., `NEW`, `PARTIALLY_FILLED`). 