# Place New Order (Spot)

This endpoint is used to send in new orders to the Spot market.

## Endpoint

*   **`POST /api/v3/order`** (Verify exact endpoint in official Spot API docs)

## Base URLs

*   `https://api.binance.com` (Primary)
*   `https://api1.binance.com`
*   `https://api2.binance.com`
*   `https://api3.binance.com`
*   `https://api4.binance.com`

## Security Type

*   **`TRADE`** (Requires API Key and Signature)

## Parameters

*(Note: This is a common set of parameters based on general exchange APIs and Futures examples. Verify exact mandatory/optional parameters and enum values in official Spot documentation)*

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSDT`).
*   **`side`** (Mandatory): `BUY` or `SELL`.
*   **`type`** (Mandatory): Order type (e.g., `LIMIT`, `MARKET`, `STOP_LOSS`, `STOP_LOSS_LIMIT`, `TAKE_PROFIT`, `TAKE_PROFIT_LIMIT`, `LIMIT_MAKER`).
*   **`timeInForce`** (Optional/Required depending on type): Time in force policy (e.g., `GTC`, `IOC`, `FOK`). Required for `LIMIT`, `STOP_LOSS_LIMIT`, `TAKE_PROFIT_LIMIT`.
*   **`quantity`** (Mandatory for most types): The amount of the base asset to buy or sell.
*   **`quoteOrderQty`** (Optional/Conditional): Specify the order size in the quote asset (e.g., buy 100 USDT worth of BTC). One of `quantity` or `quoteOrderQty` must be specified for `MARKET` orders.
*   **`price`** (Optional/Required depending on type): The price at which to place the order. Required for `LIMIT`, `STOP_LOSS_LIMIT`, `TAKE_PROFIT_LIMIT`.
*   **`stopPrice`** (Optional/Required depending on type): Used with `STOP_LOSS`, `STOP_LOSS_LIMIT`, `TAKE_PROFIT`, `TAKE_PROFIT_LIMIT` orders.
*   **`newClientOrderId`** (Optional): A unique identifier for the order assigned by the client.
*   **`recvWindow`** (Optional): The time window (in milliseconds) during which the request is valid (max typically 60000ms).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature of all parameters.

## Response Payload

Successful order placement typically returns a confirmation object.

*(Conceptual structure - check official docs)*

```json
// Example Response (LIMIT order)
{
  "symbol": "BTCUSDT",
  "orderId": 28,
  "orderListId": -1, // OCO order ID, -1 otherwise
  "clientOrderId": "6gCrw2kRUAF9CvJDGP16IP",
  "transactTime": 1507725176595,
  "price": "0.00001000",
  "origQty": "10.00000000",
  "executedQty": "0.00000000",
  "cummulativeQuoteQty": "0.00000000",
  "status": "NEW",
  "timeInForce": "GTC",
  "type": "LIMIT",
  "side": "BUY",
  "fills": [] // Array of trade fills, empty for non-executed orders
}
```

**Important:**
*   Always refer to the [Exchange Info](./exchange-info.md) endpoint to understand symbol-specific filters (min/max quantity, price tick size, min notional value) before placing orders.
*   Ensure correct [Authentication](./../../authentication.md) (signature generation, timestamp, recvWindow). 