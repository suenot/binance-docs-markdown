# Get Candlestick (Kline) Data (COIN-M Futures)

Retrieves candlestick/kline data for a specific symbol on the COIN-M Futures market. Klines are uniquely identified by their open time.

## Endpoint

*   **`GET /dapi/v1/klines`** (Regular Klines - Verify endpoint in official COIN-M API docs)
*   **`GET /dapi/v1/continuousKlines`** (Continuous Contract Klines)
*   **`GET /dapi/v1/indexPriceKlines`** (Index Price Klines)
*   **`GET /dapi/v1/markPriceKlines`** (Mark Price Klines)

## Base URL

*   `https://dapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

### Regular Klines (`/klines`)

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSD_PERP`).
*   **`interval`** (Mandatory): The kline interval (e.g., `1m`, `5m`, `1h`, `1d`).
*   **`startTime`** (Optional): Start time in milliseconds.
*   **`endTime`** (Optional): End time in milliseconds.
*   **`limit`** (Optional): Default 500; max 1500.

### Continuous Contract Klines (`/continuousKlines`)

*   **`pair`** (Mandatory): The underlying trading pair (e.g., `BTCUSD`).
*   **`contractType`** (Mandatory): Type of contract (`PERPETUAL`, `CURRENT_QUARTER`, `NEXT_QUARTER`).
*   **`interval`** (Mandatory): The kline interval.
*   **`startTime`** (Optional)
*   **`endTime`** (Optional)
*   **`limit`** (Optional): Default 500; max 1500.

### Index/Mark Price Klines (`/indexPriceKlines`, `/markPriceKlines`)

*   **`pair`** (Mandatory): The underlying trading pair (e.g., `BTCUSD`).
*   **`interval`** (Mandatory): The kline interval.
*   **`startTime`** (Optional)
*   **`endTime`** (Optional)
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
// Example Response (Conceptual - BTCUSD_PERP)
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
*   The weight of these endpoints varies based on the `limit` parameter as per the 2020-12-30 change log.
*   For real-time kline updates, consider using the [Kline/Candlestick WebSocket Streams](./../websocket/coin-m-futures.md).
*   `continuousKlines` are useful for obtaining uninterrupted kline data for a specific contract type regardless of delivery events.
*   `indexPriceKlines` and `markPriceKlines` show the price movement of the index and mark prices respectively, which are used for settlement and liquidation calculations. 