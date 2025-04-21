# Get Account Balance (USDⓈ-M Futures)

Retrieves the asset balances for the user's USDⓈ-M Futures account.

## Endpoint

*   **`GET /fapi/v2/balance`** (or `/fapi/v1/balance` - Verify exact endpoint and version)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`USER_DATA`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Futures documentation)*

*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Returns an array of asset balance objects.

*(Conceptual structure - check official docs for exact fields, types, and precision)*

```json
// Example Response (Conceptual)
[
  {
    "accountAlias": "SgsR",       // Unique account code
    "asset": "USDT",               // Asset name
    "balance": "10000.00000000",   // Wallet balance
    "crossWalletBalance": "10000.00000000", // Crossed wallet balance
    "crossUnPnl": "0.00000000",   // Unrealized PnL of crossed positions
    "availableBalance": "9990.00000000",  // Available balance (balance - reserved)
    "maxWithdrawAmount": "9990.00000000", // Maximum amount for transfer-out
    "marginAvailable": true,       // Whether the asset can be used as margin in Multi-Assets mode
    "updateTime": 1620000000000
  },
  {
    "accountAlias": "SgsR", 
    "asset": "BUSD",
    "balance": "500.00000000",
    "crossWalletBalance": "500.00000000",
    "crossUnPnl": "0.00000000",
    "availableBalance": "500.00000000",
    "maxWithdrawAmount": "500.00000000",
    "marginAvailable": true,
    "updateTime": 1620000000000
  }
  // ... other asset balances
]
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   The `availableBalance` indicates the amount usable for new orders or withdrawals.
*   `crossWalletBalance` and `crossUnPnl` are particularly relevant for understanding margin calculations in Cross Margin mode.
*   This endpoint provides a snapshot. For real-time updates, use the [User Data WebSocket Stream](./../websocket/usds-m-futures.md) (`ACCOUNT_UPDATE` event).
*   There might be a separate endpoint like `/fapi/v1/account` or `/fapi/v2/account` which provides a more holistic view including balances, positions, and other account details in a single call. Verify with official documentation. 