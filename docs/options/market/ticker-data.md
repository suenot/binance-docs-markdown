# Options Market Data: Ticker Data

Provides 24-hour rolling window price change statistics for an Options symbol.

**Base URL:** `eapi.binance.com`

## Get 24hr Ticker Statistics

`GET /eapi/v1/ticker`

**Weight:** 5

**Parameters:**

| Name   | Type   | Mandatory | Description                                |
| ------ | ------ | --------- | ------------------------------------------ |
| symbol | STRING | NO        | Option trading pair, e.g., `BTC-200730-9000-C`. If omitted, returns data for all option symbols. |

**Response Example (Single Symbol):**

```json
[
  {
    "symbol": "BTC-200730-9000-C",
    "priceChange": "-16.2038",        // 24h Price Change
    "priceChangePercent": "-0.0162",  // 24h Price Change Percent
    "lastPrice": "1000",              // Last Traded Price
    "lastQty": "1000",                // Last Traded Quantity (Contracts)
    "open": "1016.2038",              // 24h Open Price
    "high": "1016.2038",              // 24h High Price
    "low": "0",                       // 24h Low Price
    "volume": "5",                    // 24h Volume (Contracts)
    "amount": "1",                    // 24h Volume (Quote Asset)
    "bidPrice":"999.34",              // Best Bid Price
    "askPrice":"1000.23",             // Best Ask Price
    "openTime": 1592317127349,        // First trade time in the window (ms)
    "closeTime": 1592380593516,       // Last trade time in the window (ms)
    "firstTradeId": 1,                // First Trade ID in the window
    "tradeCount": 5,                  // Total number of trades
    "strikePrice": "9000",            // Strike Price
    "exercisePrice": "3000.3356"      // Estimated settlement price (1hr before exercise), otherwise index price
  }
]
```

*Note: If `symbol` is omitted, the response will be an array containing ticker objects for all available option symbols.* 