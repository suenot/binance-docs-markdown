# Cancel Order (COIN-M Futures)

Cancel an active order for COIN-M Futures.

## Base URL
`https://dapi.binance.com`

## Security Type
[USER_DATA]

Endpoint requires your API Key and a valid signature.

## HTTP Request Method
`DELETE /dapi/v1/order`

## Parameters

**Query Parameters:**

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| symbol | STRING | YES | Trading symbol, e.g. BTCUSD_PERP |
| orderId | LONG | NO | Unique identifier for the order |
| origClientOrderId | STRING | NO | Original client order ID |
| recvWindow | LONG | NO | The value cannot be greater than 60000 |
| timestamp | LONG | YES | Current timestamp (in ms) |
| signature | STRING | YES | HMAC SHA256 signature using your API secret |

**Note:** Either `orderId` or `origClientOrderId` must be sent.

## Response
```javascript
{
  "orderId": 4612097861,
  "symbol": "BTCUSD_PERP",
  "pair": "BTCUSD",
  "status": "CANCELED",
  "clientOrderId": "7BOSEMlb00bMIuOZzWKxn2",
  "price": "37000",
  "avgPrice": "0",
  "origQty": "1",
  "executedQty": "0",
  "cumQty": "0",
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
  "time": 1645606370874,
  "updateTime": 1645606370874
}
```

## Response Fields

| Field | Type | Description |
| ----- | ---- | ----------- |
| orderId | LONG | Unique identifier for the order |
| symbol | STRING | Trading symbol |
| pair | STRING | Trading pair |
| status | STRING | Order status. Possible values include: CANCELED |
| clientOrderId | STRING | Client-generated order ID |
| price | STRING | Order price |
| avgPrice | STRING | Average filled price |
| origQty | STRING | Original order quantity |
| executedQty | STRING | Quantity of the order that has been executed |
| cumQty | STRING | Cumulative filled quantity |
| cumBase | STRING | Cumulative quote quantity |
| timeInForce | STRING | Time in force for the order |
| type | STRING | Order type (e.g., LIMIT, MARKET) |
| reduceOnly | BOOLEAN | Indicates if the order was set to reduce position only |
| closePosition | BOOLEAN | Indicates if the order was set to close position |
| side | STRING | Order side (BUY or SELL) |
| positionSide | STRING | Position side (LONG, SHORT, or BOTH) |
| stopPrice | STRING | Stop price for stop orders |
| workingType | STRING | Working type of the order price |
| priceProtect | BOOLEAN | Price protection indicator |
| origType | STRING | Original order type |
| time | LONG | Order creation time |
| updateTime | LONG | Last update time of the order |

## Notes
- Weight: 1
- If both `orderId` and `origClientOrderId` are provided, `orderId` takes precedence.
- The returned data represents the state of the canceled order.
- Orders can be canceled using either the `orderId` or the `origClientOrderId`.
- Ensure you have proper authentication and authorization before making this request. 