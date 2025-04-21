# Get Exchange Info (USDⓈ-M Futures)

Retrieves current exchange trading rules and symbol information for the USDⓈ-Margined Futures market.

## Endpoint

*   **`GET /fapi/v1/exchangeInfo`** (Verify exact endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

*   None

## Response Payload (Conceptual Structure)

The response is similar in structure to the Spot `exchangeInfo` endpoint but contains details specific to USDⓈ-M Futures.

*   Server Time
*   Rate Limits (specific to Futures API)
*   List of Symbols:
    *   Symbol name (e.g., `BTCUSDT`)
    *   Pair name (e.g., `BTCUSDT`)
    *   Contract Type (e.g., `PERPETUAL`)
    *   Delivery Date / Onboarding Date
    *   Status (e.g., `TRADING`)
    *   Base asset (e.g., `BTC`)
    *   Quote asset (e.g., `USDT`)
    *   Margin Asset (e.g., `USDT`)
    *   Price Precision
    *   Quantity Precision
    *   Base Asset Precision
    *   Quote Asset Precision
    *   Order types allowed (e.g., `LIMIT`, `MARKET`, `STOP`)
    *   Time in Force policies allowed (e.g., `GTC`, `IOC`, `FOK`)
    *   Filters (Price, Lot Size, Market Lot Size, Max Num Orders, etc.)

```json
// Example Structure - Refer to official docs for exact fields
{
  "timezone": "UTC",
  "serverTime": 1565667960030,
  "rateLimits": [
      //... Futures specific rate limits
  ],
  "exchangeFilters": [],
  "symbols": [
    {
      "symbol": "BTCUSDT",
      "pair": "BTCUSDT",
      "contractType": "PERPETUAL",
      "deliveryDate": 4133404800000,
      "onboardDate": 1569398400000,
      "status": "TRADING",
      "maintMarginPercent": "2.5000", // Liquidation margin ratio
      "requiredMarginPercent": "5.0000", // Initial margin ratio
      "baseAsset": "BTC",
      "quoteAsset": "USDT",
      "marginAsset": "USDT",
      "pricePrecision": 2, // Price decimals
      "quantityPrecision": 3, // Quantity decimals
      "baseAssetPrecision": 8,
      "quotePrecision": 8,
      "orderTypes": [
        "LIMIT",
        "MARKET",
        "STOP",
        // ... other types
      ],
      "timeInForce": [
        "GTC",
        "IOC",
        "FOK",
        "GTX"
      ],
      "filters": [
         // ... various Futures specific filters ...
      ]
    },
    // ... other symbols
  ]
}
```

**Note:** This endpoint is essential for understanding contract specifications and trading rules (tick sizes, step sizes, margin requirements) before interacting with the Futures market. 