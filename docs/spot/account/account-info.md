# Get Account Information (Spot)

Retrieves current account information, including balances and permissions for the Spot account.

## Endpoint

*   **`GET /api/v3/account`** (Verify exact endpoint in official Spot API docs)

## Base URLs

*   `https://api.binance.com` (Primary)
*   `https://api1.binance.com`
*   `https://api2.binance.com`
*   `https://api3.binance.com`
*   `https://api4.binance.com`

## Security Type

*   **`USER_DATA`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Spot documentation)*

*   **`recvWindow`** (Optional): The time window (in milliseconds) during which the request is valid (max typically 60000ms).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature of all parameters.

## Response Payload

Returns an object containing account details.

*(Conceptual structure - check official docs for exact fields)*

```json
// Example Response (Conceptual)
{
  "makerCommission": 15,
  "takerCommission": 15,
  "buyerCommission": 0,
  "sellerCommission": 0,
  "canTrade": true,
  "canWithdraw": true,
  "canDeposit": true,
  "updateTime": 123456789,
  "accountType": "SPOT",
  "balances": [
    {
      "asset": "BTC",
      "free": "4723846.89208129",
      "locked": "0.00000000"
    },
    {
      "asset": "LTC",
      "free": "4763368.68006011",
      "locked": "0.00000000"
    },
    // ... other balances
  ],
  "permissions": [
    "SPOT"
  ]
}
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   The `balances` array includes all assets, even those with zero balance.
*   `free` indicates the amount available for trading/withdrawal.
*   `locked` indicates the amount currently tied up in open orders. 