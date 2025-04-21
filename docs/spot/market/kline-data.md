# Get Candlestick (Kline) Data (Spot)

This endpoint retrieves candlestick/kline data for a symbol. Candlesticks are uniquely identified by their open time.

## Endpoint

*   **`GET /api/v3/klines`**
*   *Also potentially `GET /api/v3/uiKlines` (Purpose might differ slightly, e.g., optimized for UI display - check official docs)*

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

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSDT`).
*   **`interval`** (Mandatory): The kline interval (e.g., `1m`, `5m`, `1h`, `1d`).
*   **`startTime`** (Optional): Start time in milliseconds.
*   **`endTime`** (Optional): End time in milliseconds.
*   **`limit`** (Optional): Default 500; max 1000.

## Response Payload

The response is an array of arrays, where each inner array represents a single kline.

Data is returned in **ascending** order (oldest first).

Each inner array contains:

1.  `Kline open time` (Milliseconds)
2.  `Open price`
3.  `High price`
4.  `Low price`
5.  `Close price`
6.  `Volume`
7.  `Kline close time` (Milliseconds)
8.  `Quote asset volume`
9.  `Number of trades`
10. `Taker buy base asset volume`
11. `Taker buy quote asset volume`
12. `Ignore` (Can be ignored)

```json
// Example Response (Partial)
[
  [
    1499040000000,      // Open time
    "0.01634790",       // Open
    "0.80000000",       // High
    "0.01575800",       // Low
    "0.01577100",       // Close
    "148976.11427815",  // Volume
    1499644799999,      // Close time
    "2434.19055334",    // Quote asset volume
    308,                // Number of trades
    "1756.87402397",    // Taker buy base asset volume
    "28.46694368",      // Taker buy quote asset volume
    "0"                 // Ignore
  ],
  // ... more klines
]
```

**Notes:**
*   If `startTime` and `endTime` are not sent, the most recent klines are returned.
*   The `uiKlines` endpoint might have variations; consult official documentation for its specific use case and response format if different. 