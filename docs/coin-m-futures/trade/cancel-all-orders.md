# Cancel All Open Orders (COIN-M Futures)

Cancel all open orders on a specific symbol for COIN-M Futures.

## Base URL
`https://dapi.binance.com`

## Security Type
[TRADE]

Endpoint requires your API Key and a valid signature.

## HTTP Request Method
`DELETE /dapi/v1/allOpenOrders`

## Parameters

**Query Parameters:**

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| symbol | STRING | YES | Trading symbol, e.g. BTCUSD_PERP |
| recvWindow | LONG | NO | The value cannot be greater than 60000 |
| timestamp | LONG | YES | Current timestamp (in ms) |
| signature | STRING | YES | HMAC SHA256 signature using your API secret |

## Response

A successful cancellation returns a success message:

```javascript
{
  "code": "200",
  "msg": "The operation of cancel all open order is done."
}
```

## Error Responses

If the operation fails, an error message will be returned, for example:

```javascript
{
  "code": -4046,
  "msg": "No need to cancel open orders."
}
```

This error typically occurs if there are no open orders on the specified symbol to cancel.

## Notes
- Weight: 1
- This endpoint cancels **all** open orders for the specified `symbol`.
- Ensure proper authentication and authorization. 