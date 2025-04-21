---
title: Cancel Option Order (TRADE)
sidebar_label: Cancel Order
sidebar_position: 2
---

# Cancel Option Order (TRADE)

Cancel an active order.

**HTTP Method:** `DELETE`
**Endpoint:** `/eapi/v1/order`
**Weight:** 1
**Signed:** Yes (TRADE)

## Request Parameters

| Name          | Type   | Mandatory | Description                                                  | Example                   |
|---------------|--------|-----------|--------------------------------------------------------------|---------------------------|
| symbol        | STRING | YES       | Option trading pair                                          | `BTC-200730-9000-C`       |
| orderId       | LONG   | NO        | System order ID                                              | `4611875134427365377`     |
| clientOrderId | STRING | NO        | User-defined order ID                                        | `my_cancel_order_id_1`    |
| recvWindow    | LONG   | NO        | The time window (in milliseconds) for which the request is valid. Defaults to 5000. | `5000`                    |
| timestamp     | LONG   | YES       | Request timestamp (in milliseconds)                          | `1628888888888`           |

:::info
At least one of `orderId` or `clientOrderId` must be sent.
:::

## Response Example

```json
{
  "orderId": 4611875134427365377,
  "symbol": "BTC-200730-9000-C",
  "price": "100",
  "quantity": "1",
  "executedQty": "0",
  "fee": "0",
  "side": "BUY",
  "type": "LIMIT",
  "timeInForce": "GTC",
  "reduceOnly": false,
  "postOnly": false,
  "createDate": 1592465880683,
  "updateTime": 1566818724722,
  "status": "CANCELLING", // Status upon successful cancellation request, may become CANCELLED later
  "avgPrice": "0",
  "source": "API",
  "clientOrderId": "",
  "priceScale": 4,
  "quantityScale": 4,
  "optionSide": "CALL",
  "quoteAsset": "USDT",
  "mmp": false
}
``` 