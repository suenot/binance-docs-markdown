# Query Order (COIN-M Futures)

You can query the details of a specific order on the COIN-M Futures market.

## Base URL

`https://dapi.binance.com`

## Security Type

TRADE - Endpoint requires API Key and signature.

## Method

GET /dapi/v1/order

## Parameters

**Query Parameters**:

| Parameter           | Type    | Required | Description |
|---------------------|---------|----------|-------------|
| symbol              | STRING  | YES      | The trading pair name |
| orderId             | LONG    | NO*      | Order ID |
| origClientOrderId   | STRING  | NO*      | Client order ID |
| timestamp           | LONG    | YES      | Current timestamp (in milliseconds) |
| signature           | STRING  | YES      | HMAC SHA256 signature using the secret key |

\* Note: Either `orderId` or `origClientOrderId` must be provided.

## Response Payload

```json
{
  "orderId": 4022044081,
  "symbol": "BTCUSD_PERP",
  "pair": "BTCUSD",  
  "status": "FILLED",
  "clientOrderId": "testOrder",
  "price": "23416.10",
  "avgPrice": "23416.10000",
  "origQty": "1",
  "executedQty": "1",
  "cumQty": "1",
  "cumBase": "0.00042705",
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
  "time": 1669202762447,
  "updateTime": 1669202762447
}
```

## Response Fields

| Field          | Type    | Description |
|----------------|---------|-------------|
| orderId        | LONG    | Order ID |
| symbol         | STRING  | Trading pair name |
| pair           | STRING  | Base asset in the trading pair |
| status         | STRING  | Order status (e.g., NEW, PARTIALLY_FILLED, FILLED, CANCELED, REJECTED) |
| clientOrderId  | STRING  | User-provided identifier for the order |
| price          | STRING  | Order price |
| avgPrice       | STRING  | Average fill price |
| origQty        | STRING  | Original order quantity |
| executedQty    | STRING  | Executed quantity of the order |
| cumQty         | STRING  | Cumulative filled quantity |
| cumBase        | STRING  | Cumulative filled quantity in base asset |
| timeInForce    | STRING  | Time in force (GTC, IOC, FOK) |
| type           | STRING  | Order type (LIMIT, MARKET, STOP, etc.) |
| reduceOnly     | BOOLEAN | True if the order is set to reduce position only |
| closePosition  | BOOLEAN | True if the order is to close position |
| side           | STRING  | Order side (BUY or SELL) |
| positionSide   | STRING  | Position side (BOTH, LONG, or SHORT) |
| stopPrice      | STRING  | Stop price for STOP orders |
| workingType    | STRING  | Working type of the order price |
| priceProtect   | BOOLEAN | True if price protection is triggered |
| origType       | STRING  | Original order type |
| time           | LONG    | Order creation time |
| updateTime     | LONG    | Order update time |

## Error Responses

| HTTP Code | Error Code | Description |
|-----------|------------|-------------|
| 400       | -2013      | Order does not exist |

## Notes

- Either `orderId` or `origClientOrderId` must be provided to identify the order.
- If submitting `origClientOrderId`, make sure the value matches the `clientOrderId` that was sent with the original order.
- Timestamps used for signatures must be within 1000ms of the server time. 