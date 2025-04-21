# Get Margin Account Details (Spot)

Retrieves details for the Spot Margin account (Cross or Isolated).

## Endpoint

*   **`GET /sapi/v1/margin/account`** (For Cross Margin - Verify)
*   **`GET /sapi/v1/margin/isolated/account`** (For Isolated Margin - Verify)

*Note: Separate endpoints might exist for Cross and Isolated Margin accounts. Verify exact endpoints in official Margin API docs.* 

## Base URLs

*   *(Likely `https://api.binance.com` and alternatives, but verify - SAPI endpoints might have different base URLs or restrictions)*
*   `https://api.binance.com` (Primary Assumption)

## Security Type

*   **`MARGIN`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Margin documentation)*

*   **For Isolated:** `symbols` (Optional): Max 5 symbols, comma-separated (e.g., `BTCUSDT,BNBBTC`). Returns all isolated accounts if omitted.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Returns details about the margin account status.

*(Conceptual structure - check official docs for exact fields for both Cross and Isolated)*

**Cross Margin (Conceptual):**

```json
// Example Response (Conceptual - Cross)
{
  "borrowEnabled": true,
  "marginLevel": "11.64405621",
  "totalAssetOfBtc": "6.82728454",
  "totalLiabilityOfBtc": "0.58633215",
  "totalNetAssetOfBtc": "6.24095239",
  "tradeEnabled": true,
  "transferEnabled": true,
  "userAssets": [
    {
      "asset": "BTC",
      "borrowed": "0.00000000",
      "free": "0.00000000",
      "interest": "0.00000000",
      "locked": "0.00000000",
      "netAsset": "0.00000000"
    },
    // ... other assets
  ]
}
```

**Isolated Margin (Conceptual):**

```json
// Example Response (Conceptual - Isolated)
{
  "assets": [
    {
      "baseAsset": { // Base asset details
        "asset": "BTC", 
        // ... balances (borrowed, free, interest, locked, netAsset)
      },
      "quoteAsset": { // Quote asset details
        "asset": "USDT",
        // ... balances
      },
      "symbol": "BTCUSDT",
      "isolatedCreated": true,
      "enabled": true, // Whether trade is enabled
      "marginLevel": "2.16747979",
      "marginLevelStatus": "EXCESSIVE", // NORMAL, MARGIN_CALL, PRE_LIQUIDATION, FORCE_LIQUIDATION
      "marginRatio": "1.85162609",
      "indexPrice": "40000", // Used for margin calculation
      "liquidatePrice": "15000", // Liquidation price
      "liquidateRate": "1.05", // Liquidation rate
      "tradeEnabled": true
    },
    // ... other isolated pairs
  ],
  "totalAssetOfBtc": "...", // Optional, if querying all
  "totalLiabilityOfBtc": "...", // Optional, if querying all
  "totalNetAssetOfBtc": "..." // Optional, if querying all
}

```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   Response structure differs significantly between Cross and Isolated margin endpoints.
*   Understand fields like `marginLevel`, `totalAssetOfBtc`, `totalLiabilityOfBtc`, `liquidatePrice` to manage margin risk. 