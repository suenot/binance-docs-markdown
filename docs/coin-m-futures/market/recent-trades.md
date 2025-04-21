# Get Recent Trades List (COIN-M Futures)

Retrieves the most recent trades for a specific symbol on the COIN-M Futures market.

## Endpoint

*   **`GET /dapi/v1/trades`** (Verify endpoint in official COIN-M API docs)

## Base URL

*   `https://dapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSD_PERP`, `ETHUSD_241227`).
*   **`limit`** (Optional): Default 500; max 1000.

## Response Payload

The response is an array of trade objects, each containing details about a single trade.

*   `id`: Trade ID.
*   `price`: Price at which the trade occurred.
*   `qty`: Quantity traded (in contracts).
*   `quoteQty`: Quote asset quantity (price * qty).
*   `time`: Timestamp of the trade (milliseconds).
*   `isBuyerMaker`: Boolean indicating if the buyer was the maker.

```json
// Example Response (Conceptual - BTCUSD_PERP)
[
  {
    "id": 28457,
    "price": "9000.1",
    "qty": "150",
    "quoteQty": "1350015", // For BTCUSD contracts, this represents the USD value
    "time": 1591702614000,
    "isBuyerMaker": true
  },
  // ... more trades
]
```

**Important:**
*   This endpoint retrieves public trade data, not account-specific trades.
*   For real-time trade updates, consider using the [Aggregate Trade or Trade WebSocket Streams](./../websocket/coin-m-futures.md).
*   For historical trades beyond the limit, check official documentation for endpoints like `/dapi/v1/historicalTrades` or `/dapi/v1/aggTrades`.
*   The weight of the `historicalTrades` endpoint was updated to 20 as per the 2020-12-30 change log.
*   The `qty` field represents the number of contracts traded, not the base asset amount. 