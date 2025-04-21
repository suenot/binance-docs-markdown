# Place New Order (COIN-M Futures)

Sends in a new order to the COIN-M Futures market.

## Endpoint

*   **`POST /dapi/v1/order`** (Verify endpoint in official COIN-M API docs)

## Base URL

*   `https://dapi.binance.com`

## Security Type

*   **`TRADE`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters and enum values in official COIN-M documentation)*

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSD_PERP`, `ETHUSD_241227`).
*   **`side`** (Mandatory): `BUY` or `SELL`.
*   **`positionSide`** (Optional, Mandatory in Hedge Mode): `BOTH`, `LONG`, `SHORT`. Defaults to `BOTH` if Hedge Mode is disabled.
*   **`type`** (Mandatory): Order type (e.g., `LIMIT`, `MARKET`, `STOP`, `STOP_MARKET`, `TAKE_PROFIT`, `TAKE_PROFIT_MARKET`, `TRAILING_STOP_MARKET`).
*   **`timeInForce`** (Optional/Required depending on type): Time in force policy (e.g., `GTC`, `IOC`, `FOK`, `GTX`).
*   **`quantity`** (Mandatory for most types): The quantity in contract units.
*   **`reduceOnly`** (Optional): `true` or `false`. Default `false`. Cannot be sent with `closePosition`.
*   **`price`** (Optional/Required depending on type): Limit price.
*   **`newClientOrderId`** (Optional): A unique identifier for the order assigned by the client. The regular expression rule updated as `^[\.A-Z\:/a-z0-9_-]{1,36}$` (2021-01-21).
*   **`stopPrice`** (Optional/Required depending on type): Used with `STOP`, `STOP_MARKET`, `TAKE_PROFIT`, `TAKE_PROFIT_MARKET` orders.
*   **`closePosition`** (Optional): `true` or `false`. If true, closes the existing position. Invalid if `quantity` is specified.
*   **`activationPrice`** (Optional): Used with `TRAILING_STOP_MARKET` orders.
*   **`callbackRate`** (Optional): Used with `TRAILING_STOP_MARKET` orders.
*   **`workingType`** (Optional): `MARK_PRICE`, `CONTRACT_PRICE`. Default `CONTRACT_PRICE`.
*   **`priceProtect`** (Optional): `true` or `false`. Used with `STOP_MARKET` or `TAKE_PROFIT_MARKET` orders.
*   **`newOrderRespType`** (Optional): `ACK` or `RESULT`. Default `ACK`. `RESULT` returns the final order status.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

**Additional mandatory parameters based on `type`:**

| Type                              | Additional mandatory parameters |
| --------------------------------- | ------------------------------- |
| LIMIT                             | timeInForce, quantity, price    |
| MARKET                            | quantity                        |
| STOP/TAKE_PROFIT                  | price, stopPrice                |
| STOP_MARKET/TAKE_PROFIT_MARKET    | stopPrice                       |
| TRAILING_STOP_MARKET              | callbackRate                    |

## Response Payload

Successful order placement returns a confirmation. Format depends on `newOrderRespType`.

*(Conceptual structure - check official docs)*

**`newOrderRespType=ACK` (Default):**
```json
{
    "orderId": 2831942115,
    "symbol": "BTCUSD_PERP",
    "status": "NEW",
    "clientOrderId": "x-J1O8XyRRZ",
    "price": "50000",
    "avgPrice": "0.00000",
    "origQty": "1",
    "executedQty": "0",
    "cumBase": "0",
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
    "updateTime": 1628099790000 
}
```

**`newOrderRespType=RESULT` (Conceptual - may differ for MARKET vs LIMIT):**
```json
// For MARKET order or certain LIMIT TIF
{
    // Similar fields, but status reflects final state (e.g., FILLED)
    "status": "FILLED", 
    "avgPrice": "50123.4",
    "executedQty": "1",
    "cumBase": "0.01998", 
    // ... potentially includes fill details
}
```

**Important:**
*   Always refer to [Exchange Info](./exchange-info.md) for symbol rules.
*   Understand [Hedge Mode vs One-way Mode](https://www.binance.com/en/support/faq/hedge-mode-360038201091) (Link needs verification) and the `positionSide` parameter.
*   **Trigger Conditions for Orders:**
    *   `STOP`, `STOP_MARKET`:
        *   BUY: latest price >= `stopPrice`
        *   SELL: latest price <= `stopPrice`
    *   `TAKE_PROFIT`, `TAKE_PROFIT_MARKET`:
        *   BUY: latest price <= `stopPrice`
        *   SELL: latest price >= `stopPrice`
    *   `TRAILING_STOP_MARKET`:
        *   BUY: lowest price <= `activationPrice`, then latest price >= lowest price * (1 + `callbackRate`)
        *   SELL: highest price >= `activationPrice`, then latest price <= highest price * (1 - `callbackRate`)
*   For `TRAILING_STOP_MARKET`, error code -2021 means order would trigger immediately.
*   When using `priceProtect=true`, the difference rate between mark price and contract price must be smaller than the symbol's `triggerProtect` value.
*   `STOP_MARKET` and `TAKE_PROFIT_MARKET` with `closePosition=true` will close all current position. Cannot be used with `quantity` or `reduceOnly`.
*   Ensure correct [Authentication](./../../authentication.md). 