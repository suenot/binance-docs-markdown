# Get Recent Trades List (USDⓈ-M Futures)

Retrieves the most recent trades for a specific symbol on the USDⓈ-M Futures market.

## Endpoint

*   **`GET /fapi/v1/trades`** (Verify exact endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSDT`).
*   **`limit`** (Optional): Default 500; max 1000.

## Response Payload

The response is an array of trade objects, each containing details about a single trade.

*   `id`: Trade ID.
*   `price`: Price at which the trade occurred.
*   `qty`: Quantity traded (in base asset).
*   `quoteQty`: Quote asset quantity (price * qty).
*   `time`: Timestamp of the trade (milliseconds).
*   `isBuyerMaker`: Boolean indicating if the buyer was the maker.

```json
// Example Response (Conceptual)
[
  {
    "id": 28457,
    "price": "9700.01",
    "qty": "1.2",
    "quoteQty": "11640.012",
    "time": 1589436922972,
    "isBuyerMaker": true
  },
  // ... more trades
]
```

**Note:**
*   This endpoint retrieves public trade data, not account-specific trades.
*   For real-time trade updates, consider using the [Aggregate Trade or Trade WebSocket Streams](./../websocket/usds-m-futures.md).
*   For historical trades beyond the limit, check official documentation for endpoints like `/fapi/v1/historicalTrades` or `/fapi/v1/aggTrades`. 