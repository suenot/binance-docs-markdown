# Change Margin Type (COIN-M Futures)

Modify the margin type (ISOLATED or CROSSED) for a specific symbol in the COIN-M Futures market.

## Base URL
`https://dapi.binance.com`

## Security Type
[TRADE]

Requires API Key and Signature.

## HTTP Request Method
`POST /dapi/v1/marginType`

## Parameters

**Query Parameters:**

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| symbol | STRING | YES | Trading symbol, e.g., BTCUSD_PERP |
| marginType | ENUM | YES | `ISOLATED` or `CROSSED` |
| recvWindow | LONG | NO | The value cannot be greater than 60000 |
| timestamp | LONG | YES | Current timestamp (in ms) |
| signature | STRING | YES | HMAC SHA256 signature using your API secret |

## Response

A successful request returns a success code.

**Example Response:**

```javascript
{
  "code": 200,
  "msg": "success"
}
```

## Error Responses

Common errors include trying to change margin type while having open positions or orders.

```javascript
{
  "code": -4047,
  "msg": "Margin type cannot be changed if there exists position."
}
```

## Notes
- Weight: 1
- You cannot change the margin type if you have open positions or open orders for the specified symbol.
- Ensure you close all relevant positions and orders before attempting to change the margin type. 