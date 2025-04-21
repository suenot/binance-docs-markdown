# Get Exchange Info (Spot)

This endpoint retrieves current exchange trading rules and symbol information for the Spot market.

## Endpoint

*   **`GET /api/v3/exchangeInfo`**

## Base URLs

*   `https://api.binance.com` (Primary)
*   `https://api1.binance.com`
*   `https://api2.binance.com`
*   `https://api3.binance.com`
*   `https://api4.binance.com`
*   `https://data-api.binance.vision` (Data-specific endpoint)

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

*   None (or optional `symbol` / `symbols` - verify official docs)

## Response Payload (Conceptual Structure)

The response contains comprehensive details about the exchange, including:

*   Server Time
*   Rate Limits currently applied
*   List of Symbols:
    *   Symbol name (e.g., `BTCUSDT`)
    *   Status (e.g., `TRADING`)
    *   Base asset (e.g., `BTC`)
    *   Quote asset (e.g., `USDT`)
    *   Order types allowed (e.g., `LIMIT`, `MARKET`, `STOP_LOSS`)
    *   Trading permissions (e.g., `SPOT`, `MARGIN`)
    *   Filters:
        *   Price filter (min/max price, tick size)
        *   Lot size filter (min/max quantity, step size)
        *   Market lot size filter
        *   Min notional filter
        *   And others...

```json
// Example Structure - Refer to official docs for exact fields
{
  "timezone": "UTC",
  "serverTime": 1672531200000,
  "rateLimits": [
    // ... rate limit details ...
  ],
  "exchangeFilters": [
    // ... global exchange filters ... 
  ],
  "symbols": [
    {
      "symbol": "BTCUSDT",
      "status": "TRADING",
      "baseAsset": "BTC",
      "baseAssetPrecision": 8,
      "quoteAsset": "USDT",
      "quotePrecision": 8,
      "quoteAssetPrecision": 8,
      "orderTypes": [
        "LIMIT",
        "LIMIT_MAKER",
        "MARKET",
        // ... other order types
      ],
      "icebergAllowed": true,
      "ocoAllowed": true,
      "isSpotTradingAllowed": true,
      "isMarginTradingAllowed": true,
      "filters": [
        // ... various filters (price, lot size, etc.) ...
      ],
      "permissions": [
        "SPOT",
        "MARGIN"
      ]
    },
    // ... other symbols ...
  ]
}
```

**Note:** This endpoint is crucial for understanding trading constraints (min/max order sizes, price increments) before placing orders. 