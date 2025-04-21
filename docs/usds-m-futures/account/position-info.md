# Get Position Information (USDⓈ-M Futures)

Retrieves information about the user's open positions in the USDⓈ-M Futures market.

## Endpoint

*   **`GET /fapi/v2/positionRisk`** (or `/fapi/v1/positionRisk` - Verify exact endpoint and version)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`USER_DATA`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Futures documentation)*

*   **`symbol`** (Optional): If provided, only the position for this symbol is returned.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Returns an array of position objects. If `symbol` is specified, returns an array with a single object (or empty if no position).

*(Conceptual structure - check official docs for exact fields and types)*

```json
// Example Response (Conceptual)
[
  {
    "symbol": "BTCUSDT",
    "positionAmt": "0.100",      // Position amount (positive for long, negative for short)
    "entryPrice": "50000.0",    // Average entry price
    "markPrice": "50500.0",      // Current mark price
    "unRealizedProfit": "50.00", // Unrealized PnL
    "liquidationPrice": "45000.0",// Liquidation price
    "leverage": "10",            // Current leverage
    "marginType": "isolated",    // "isolated" or "cross"
    "isolatedMargin": "500.00",  // Isolated margin (if applicable)
    "isAutoAddMargin": "false",  // Whether auto margin add is enabled (for isolated)
    "positionSide": "BOTH",      // Position side: BOTH, LONG, SHORT (relevant in Hedge Mode)
    "updateTime": 1620000000000 // Last update time
  },
  // ... other positions if symbol was not specified
]
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   Positions with `positionAmt` = 0 might still be returned if there's isolated margin or unrealized PnL.
*   Understanding `marginType` (Cross vs. Isolated) and `positionSide` (Hedge Mode vs. One-way) is crucial for interpreting the response. See official Binance Futures documentation for details.
*   This endpoint provides a snapshot. For real-time updates, use the [User Data WebSocket Stream](./../websocket/usds-m-futures.md) (`ACCOUNT_UPDATE` event).
*   There might be a separate endpoint like `/fapi/v1/account` which provides a more holistic view including balances and position summaries. Verify with official documentation. 