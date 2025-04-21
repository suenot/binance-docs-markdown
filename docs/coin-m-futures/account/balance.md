# Get Account Balance (COIN-M Futures)

Retrieve the balance for a COIN-M Futures account.

## Base URL
`https://dapi.binance.com`

## Security Type
[USER_DATA]

Requires API Key and Signature.

## HTTP Request Method
`GET /dapi/v1/balance`

## Parameters

**Query Parameters:**

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| recvWindow | LONG | NO | The value cannot be greater than 60000 |
| timestamp | LONG | YES | Current timestamp (in ms) |
| signature | STRING | YES | HMAC SHA256 signature using your API secret |

## Response

Returns an array of asset balance objects.

**Example Response:**

```javascript
[
  {
    "accountAlias": "SgsR", // unique account code
    "asset": "BTC", // asset name
    "balance": "1.00000000", // wallet balance
    "withdrawAvailable": "1.00000000", // available withdraw amount
    "crossWalletBalance": "1.00000000", // crossed wallet balance
    "crossUnPnl": "0.00000000", // unrealized profit of crossed positions
    "availableBalance": "1.00000000", // available balance
    "updateTime": 1617936249376 // last update time
  },
  {
    "accountAlias": "SgsR", 
    "asset": "ETH", 
    "balance": "10.00000000",
    "withdrawAvailable": "10.00000000",
    "crossWalletBalance": "10.00000000",
    "crossUnPnl": "0.00000000",
    "availableBalance": "10.00000000", 
    "updateTime": 1617936249376
  }
]
```

## Notes
- Weight: 5
- This endpoint provides the current balance for each asset held in the COIN-M Futures account.
- `availableBalance` refers to the balance that can be used for placing new orders.
- `crossWalletBalance` is relevant for cross margin mode. 