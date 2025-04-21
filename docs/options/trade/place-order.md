# Options Trading: New Order (TRADE)

Sends a new order to the Binance Options exchange.

**Base URL:** `eapi.binance.com`

**Security:** TRADE (Requires API Key and Signature)

## Place New Order

`POST /eapi/v1/order`

**Weight:** 1 (per order)

**Parameters:**

| Name             | Type    | Mandatory | Description                                                |
| ---------------- | ------- | --------- | ---------------------------------------------------------- |
| `symbol`         | STRING  | YES       | Option trading pair, e.g., `BTC-200730-9000-C`             |
| `side`           | ENUM    | YES       | `BUY` or `SELL`                                            |
| `type`           | ENUM    | YES       | Order Type: `LIMIT` (Only LIMIT is supported currently)    |
| `quantity`       | DECIMAL | YES       | Order quantity (in contracts)                              |
| `price`          | DECIMAL | YES (for LIMIT) | Order price                                                |
| `timeInForce`    | ENUM    | YES (for LIMIT) | Time in force: `GTC` (Good Till Cancel), `IOC` (Immediate Or Cancel), `FOK` (Fill Or Kill). Default `GTC`. |
| `reduceOnly`     | BOOLEAN | NO        | `true` or `false`. Default `false`.                        |
| `postOnly`       | BOOLEAN | NO        | `true` or `false`. Default `false`.                        |
| `newOrderRespType`| ENUM    | NO        | Response type: `ACK` or `RESULT`. Default `ACK`.           |
| `clientOrderId`  | STRING  | NO        | A unique user-defined ID for the order.                    |
| `isMmp`          | BOOLEAN | NO        | Market Maker Protection order: `true` or `false`. Default `false`. |
| `recvWindow`     | LONG    | NO        | The time window (in ms) the request is valid for. Default 5000. |
| `timestamp`      | LONG    | YES       | Request timestamp (in ms).                                 |

**Mandatory Parameters based on Order Type:**

| Type  | Mandatory parameters   |
| ----- | ---------------------- |
| LIMIT | `timeInForce`, `quantity`, `price` |

**Response Example (ACK):**

```json
{
  "orderId": 4611875134427365377,     // System Order ID
  "symbol": "BTC-200730-9000-C",
  "price": "100",
  "quantity": "1",
  "side": "BUY",
  "type": "LIMIT",
  "createDate": 1592465880683,        // Order creation time (ms)
  "reduceOnly": false,
  "postOnly": false,
  "mmp": false
}
```

**Response Example (RESULT):**

```json
{
  "orderId": 4611875134427365377,     // System Order ID
  "symbol": "BTC-200730-9000-C",
  "price": "100",
  "quantity": "1",
  "executedQty": "0",                 // Executed quantity
  "fee": "0",                         // Order fee
  "side": "BUY",
  "type": "LIMIT",
  "timeInForce": "GTC",
  "reduceOnly": false,
  "postOnly": false,
  "createTime": 1592465880683,        // Order creation time (ms)
  "updateTime": 1566818724722,        // Last update time (ms)
  "status": "ACCEPTED",               // Order status
  "avgPrice": "0",                    // Average fill price
  "clientOrderId": "",                 // Client Order ID
  "priceScale": 2,
  "quantityScale": 2,
  "optionSide": "CALL",
  "quoteAsset": "USDT",
  "mmp": false
}
``` 