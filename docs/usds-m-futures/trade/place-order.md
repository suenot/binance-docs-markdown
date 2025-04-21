# Place New Order (USDⓈ-M Futures)

Sends in a new order to the USDⓈ-Margined Futures market.

## Endpoint

*   **`POST /fapi/v1/order`** (Verify endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`TRADE`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters and enum values in official Futures documentation)*

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSDT`).
*   **`side`** (Mandatory): `BUY` or `SELL`.
*   **`positionSide`** (Optional, Mandatory in Hedge Mode): `BOTH`, `LONG`, `SHORT`. Defaults to `BOTH` if Hedge Mode is disabled.
*   **`type`** (Mandatory): Order type (e.g., `LIMIT`, `MARKET`, `STOP`, `STOP_MARKET`, `TAKE_PROFIT`, `TAKE_PROFIT_MARKET`, `TRAILING_STOP_MARKET`).
*   **`timeInForce`** (Optional/Required depending on type): Time in force policy (e.g., `GTC`, `IOC`, `FOK`).
*   **`quantity`** (Mandatory for most types, except `MARKET` by `quoteOrderQty`): The amount of the base asset.
*   **`reduceOnly`** (Optional): `true` or `false`. Default `false`. Cannot be sent with `newOrderRespType`=`RESULT`.
*   **`price`** (Optional/Required depending on type): Limit price.
*   **`newClientOrderId`** (Optional): A unique identifier for the order assigned by the client.
*   **`stopPrice`** (Optional/Required depending on type): Used with `STOP`, `STOP_MARKET`, `TAKE_PROFIT`, `TAKE_PROFIT_MARKET` orders.
*   **`closePosition`** (Optional): `true` or `false`. If true, closes the existing position. Invalid if `quantity` is specified.
*   **`activationPrice`** (Optional): Used with `TRAILING_STOP_MARKET` orders.
*   **`callbackRate`** (Optional): Used with `TRAILING_STOP_MARKET` orders.
*   **`workingType`** (Optional): `MARK_PRICE`, `CONTRACT_PRICE`. Default `CONTRACT_PRICE`.
*   **`priceProtect`** (Optional): `true` or `false`. Used with `STOP_MARKET` or `TAKE_PROFIT_MARKET` orders.
*   **`newOrderRespType`** (Optional): `ACK` or `RESULT`. Default `ACK`. `RESULT` returns the final order status (FILLED/EXPIRED for certain types).
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Successful order placement returns a confirmation. Format depends on `newOrderRespType`.

*(Conceptual structure - check official docs)*

**`newOrderRespType=ACK` (Default):**
```json
{
    "orderId": 2831942115,
    "symbol": "BTCUSDT",
    "status": "NEW",
    "clientOrderId": "myOrder1",
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

**`newOrderRespType=RESULT` (Conceptual - may differ for MARKET vs LIMIT):**
```json
// For MARKET order or certain LIMIT TIF
{
    // Similar fields, but status reflects final state (e.g., FILLED)
    "status": "FILLED", 
    "avgPrice": "9001.5",
    "executedQty": "0.001",
    "cumQuote": "9.0015", 
    // ... potentially includes fill details
}
```

**Important:**
*   Always refer to [Exchange Info](./exchange-info.md) for symbol rules.
*   Understand [Hedge Mode vs One-way Mode](https://www.binance.com/en/support/faq/hedge-mode-360038201091) (Link needs verification) and the `positionSide` parameter.
*   Ensure correct [Authentication](./../../authentication.md). 