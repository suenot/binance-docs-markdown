# Get Candlestick (Kline) Data (USDⓈ-M Futures)

Retrieves candlestick/kline data for a specific symbol on the USDⓈ-M Futures market. Kline are uniquely identified by their open time.

## Endpoint

*   **`GET /fapi/v1/klines`** (Verify exact endpoint in official Futures API docs)
*   *(May also exist: `/fapi/v1/continuousKlines`, `/fapi/v1/indexPriceKlines`, `/fapi/v1/markPriceKlines` - check official docs for these specific kline types)*

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSDT`).
*   **`interval`** (Mandatory): The kline interval (e.g., `1m`, `5m`, `1h`, `1d`).
*   **`startTime`** (Optional): Start time in milliseconds.
*   **`endTime`** (Optional): End time in milliseconds.
*   **`limit`** (Optional): Default 500; max 1500.

## Response Payload

The response is an array of arrays, where each inner array represents a single kline. Data is returned in **ascending** order.

Each inner array contains:

1.  `Kline open time` (Milliseconds)
2.  `Open price`
3.  `High price`
4.  `Low price`
5.  `Close price` (Latest price for unfinished klines)
6.  `Volume` (In base asset)
7.  `Kline close time` (Milliseconds)
8.  `Quote asset volume`
9.  `Number of trades`
10. `Taker buy base asset volume`
11. `Taker buy quote asset volume`
12. `Ignore`

```json
// Example Response (Conceptual)
[
  [
    1591258320000, // Open time
    "9668.91",     // Open
    "9671.46",     // High
    "9668.91",     // Low
    "9671.07",     // Close
    "206.535",     // Volume
    1591258379999, // Close time
    "1997698.67",  // Quote asset volume
    253,           // Number of trades
    "100.299",     // Taker buy volume
    "970105.58",   // Taker buy quote asset volume
    "0"            // Ignore
  ],
  // ... more klines
]
```

**Notes:**
*   If `startTime` and `endTime` are not sent, the most recent klines are returned.
*   For real-time kline updates, consider using the [Kline/Candlestick WebSocket Stream](./../websocket/usds-m-futures.md). 