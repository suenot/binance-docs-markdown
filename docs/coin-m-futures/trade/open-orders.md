# Get Current Open Orders (COIN-M Futures)

This endpoint is used to retrieve all current open orders on a symbol or across all symbols for a user in the COIN-M Futures market.

**Base URL:** https://dapi.binance.com

**Security Type:** [USER_DATA]  
Requires an API Key and Signature.

## HTTP Request

`GET /dapi/v1/openOrders`

## Query Parameters for /dapi/v1/openOrders

| Parameter  | Type    | Required | Description |
|------------|---------|----------|-------------|
| symbol     | STRING  | NO       | Symbol name. If not sent, orders for all symbols will be returned |
| pair       | STRING  | NO       | Trading pair. If not sent, orders for all pairs will be returned |
| recvWindow | LONG    | NO       | The value cannot be greater than 60000 |
| timestamp  | LONG    | YES      | Current timestamp (ms) |
| signature  | STRING  | YES      | Signature for this request |

## Response

```javascript
[
  {
    "avgPrice": "0.0",
    "clientOrderId": "abc",
    "cumBase": "0",
    "executedQty": "0",
    "orderId": 1917641,
    "origQty": "0.40",
    "origType": "LIMIT",
    "price": "23416.10",
    "reduceOnly": false,
    "side": "BUY",
    "positionSide": "BOTH",
    "status": "NEW",
    "stopPrice": "0.0",
    "closePosition": false,
    "symbol": "BTCUSD_PERP",
    "pair": "BTCUSD",
    "time": 1499827319559,
    "timeInForce": "GTC",
    "type": "LIMIT",
    "activatePrice": "0.0",
    "priceRate": "0.0",
    "updateTime": 1499827319559,
    "workingType": "CONTRACT_PRICE",
    "priceProtect": false
  },
  {
    // Additional open order entries...
  }
]
```

## Response Fields

| Field           | Type    | Description |
|-----------------|---------|-------------|
| orderId         | LONG    | Order ID |
| symbol          | STRING  | Symbol name |
| pair            | STRING  | Trading pair |
| status          | STRING  | Order status. Possible values include: `NEW`, `PARTIALLY_FILLED`, `FILLED`, etc. |
| clientOrderId   | STRING  | Client order ID |
| price           | STRING  | Price |
| avgPrice        | STRING  | Average price |
| origQty         | STRING  | Original quantity |
| executedQty     | STRING  | Executed quantity |
| cumBase         | STRING  | Cumulative base asset quantity |
| timeInForce     | STRING  | Time in force |
| type            | STRING  | Order type. Possible values include: `LIMIT`, `MARKET`, `STOP`, etc. |
| origType        | STRING  | Original order type |
| activatePrice   | STRING  | Activation price, only for TRAILING_STOP_MARKET orders |
| priceRate       | STRING  | Callback rate, only for TRAILING_STOP_MARKET orders |
| updateTime      | LONG    | Last update time |
| side            | STRING  | `BUY` or `SELL` |
| positionSide    | STRING  | Position side |
| stopPrice       | STRING  | Stop price |
| workingType     | STRING  | Working type |
| priceProtect    | BOOLEAN | Price protection flag |
| reduceOnly      | BOOLEAN | Reduce only flag |
| closePosition   | BOOLEAN | Close position flag |
| time            | LONG    | Order creation time |

## Notes

- If no `symbol` or `pair` is sent, open orders for all symbols/pairs will be returned.
- Weight: 1 with symbol or pair; 40 without symbol or pair
- Max request weight for this endpoint is 1200 per minute
- When querying all open orders without a symbol or pair, the number of requests is adjusted based on the number of open orders 