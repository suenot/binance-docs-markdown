# Query Single Order (TRADE)

Check the status of a specific Options order.

**GET** `/eapi/v1/order`

**Weight:** 1

**Security:** `TRADE` (SIGNED Endpoint - requires `signature`)

## Parameters

| Name          | Type   | Mandatory | Description                                                                                                  |
|---------------|--------|-----------|--------------------------------------------------------------------------------------------------------------|
| symbol        | STRING | YES       | The specific options symbol (e.g., `BTC-231229-30000-C`)                                                     |
| orderId       | LONG   | NO        | The system-assigned order ID.                                                                                |
| clientOrderId | STRING | NO        | The user-assigned order ID.                                                                                  |
| recvWindow    | LONG   | NO        | The time window (in milliseconds) during which the request is valid. Defaults to 5000ms. Max 60000ms.        |
| timestamp     | LONG   | YES       | Request timestamp in milliseconds.                                                                           |

**Notes:**

*   Either `orderId` or `clientOrderId` **must** be sent. If both are provided, `orderId` takes precedence.

## Response Example

```json
{
    "orderId": 4611922413427359795,
    "symbol": "BTC-220715-2000-C",
    "price": "18000.00000000",
    "quantity": "-0.50000000",
    "executedQty": "-0.50000000",
    "fee": "3.00000000",
    "side": "SELL",
    "type": "LIMIT",
    "timeInForce": "GTC",
    "reduceOnly": false,
    "postOnly": false,
    "createTime": 1657867694244,
    "updateTime": 1657867888216,
    "status": "FILLED", // Possible values: NEW, PARTIALLY_FILLED, FILLED, CANCELED, REJECTED, EXPIRED
    "avgPrice": "18000.00000000",
    "source": "API",
    "clientOrderId": "my_custom_order_id_123", // Will be empty if not provided during order placement
    "priceScale": 2,
    "quantityScale": 2,
    "optionSide": "CALL", // CALL or PUT
    "quoteAsset": "USDT",
    "mmp": false // Whether the order is a Market Maker Protection order
}
```

## Potential Errors

*   `-2013`: Order does not exist.
*   `-1102`: Mandatory parameter (`symbol` or `timestamp`) was not sent, was empty/null, or malformed.
*   `-1102`: Param `orderId` or `clientOrderId` must be sent, but both were empty/null!
*   `-1121`: Invalid symbol.
*   (Refer to General Info and Error Codes for more details) 