# Change Initial Leverage (COIN-M Futures)

Adjust the initial leverage for a specific symbol or pair in the COIN-M Futures market.

## Base URL
`https://dapi.binance.com`

## Security Type
[TRADE]

Requires API Key and Signature.

## HTTP Request Method
`POST /dapi/v1/leverage`

## Parameters

**Query Parameters:**

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| symbol | STRING | YES | Trading symbol, e.g., BTCUSD_PERP |
| leverage | INT | YES | Target initial leverage: 1 to 125 |
| recvWindow | LONG | NO | The value cannot be greater than 60000 |
| timestamp | LONG | YES | Current timestamp (in ms) |
| signature | STRING | YES | HMAC SHA256 signature using your API secret |

## Response

Returns details about the leverage setting.

**Example Response:**

```javascript
{
  "leverage": 20,
  "maxQty": "100", // Based on leverage level and user's max quantity limit
  "symbol": "BTCUSD_PERP"
}
```

## Error Responses

Common errors include invalid leverage values or exceeding maximum allowed leverage for the symbol.

```javascript
{
  "code": -4048,
  "msg": "Leverage 1000 is not valid"
}
```

## Notes
- Weight: 1
- Modifying leverage may affect open positions and orders.
- Ensure the chosen leverage is within the allowed range for the specific symbol (check `GET /dapi/v1/exchangeInfo` for limits). 