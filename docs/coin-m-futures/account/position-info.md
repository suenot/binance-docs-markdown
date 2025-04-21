# Get Position Information (COIN-M Futures)

Retrieve current open positions for COIN-M Futures accounts.

## Base URL
`https://dapi.binance.com`

## Security Type
[USER_DATA]

Requires API Key and Signature.

## HTTP Request Method
`GET /dapi/v1/positionRisk`

## Parameters

**Query Parameters:**

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| symbol | STRING | NO | Trading symbol, e.g., BTCUSD_PERP. If not sent, positions for all symbols will be returned. |
| pair | STRING | NO | Base pair, e.g., BTCUSD. If not sent, positions for all symbols will be returned. |
| recvWindow | LONG | NO | The value cannot be greater than 60000 |
| timestamp | LONG | YES | Current timestamp (in ms) |
| signature | STRING | YES | HMAC SHA256 signature using your API secret |

## Response

Returns an array of position objects.

**Example Response:**

```javascript
[
  {
    "symbol": "BTCUSD_PERP",
    "positionAmt": "10",          // Position amount
    "entryPrice": "40000.0",       // Average entry price
    "markPrice": "41000.0",         // Current mark price
    "unRealizedProfit": "1000.0", // Unrealized PnL
    "liquidationPrice": "35000.0", // Liquidation price
    "leverage": "10",               // Current initial leverage
    "maxNotionalValue": "1000000",  // Maximum notional value allowed for this symbol
    "marginType": "isolated",       // isolated or cross
    "isolatedMargin": "1000.0",     // Isolated margin
    "isAutoAddMargin": "false",
    "positionSide": "BOTH",         // BOTH, LONG, SHORT
    "updateTime": 1622540000000    // Last update time
  },
  {
    "symbol": "ETHUSD_PERP",
    "positionAmt": "-5",
    "entryPrice": "2500.0",
    "markPrice": "2400.0",
    "unRealizedProfit": "500.0",
    "liquidationPrice": "3000.0",
    "leverage": "5",
    "maxNotionalValue": "500000",
    "marginType": "cross",
    "isolatedMargin": "0.0",
    "isAutoAddMargin": "false",
    "positionSide": "SHORT",
    "updateTime": 1622540100000
  }
]
```

## Notes
- Weight: 5
- Sending `symbol` or `pair` will return positions for specific symbols or pairs. If neither is sent, all positions are returned.
- If `positionAmt` is 0, it means there is no open position for that symbol.
- `positionSide` indicates the direction of the position (LONG, SHORT, or BOTH for hedge mode). 