# Get Recent Trades List (Spot)

This endpoint retrieves the most recent trades for a specific symbol on the Spot market.

## Endpoint

*   **`GET /api/v3/trades`**

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
*   **`limit`** (Optional): Default 500; max 1000.

## Response Payload

The response is an array of trade objects, each containing details about a single trade.

*   `id`: Trade ID.
*   `price`: Price at which the trade occurred.
*   `qty`: Quantity traded.
*   `quoteQty`: Quote asset quantity (price * qty).
*   `time`: Timestamp of the trade (milliseconds).
*   `isBuyerMaker`: Boolean indicating if the buyer was the maker.
*   `isBestMatch`: Boolean (utility field, often can be ignored).

```json
// Example Response (BTCUSDT, limit might return fewer if trades are sparse)
[
  {
    "id": 28457,
    "price": "4.00000100",
    "qty": "12.00000000",
    "quoteQty": "48.000012",
    "time": 1499865549590,
    "isBuyerMaker": true,
    "isBestMatch": true
  },
  // ... more trades
]
```

**Note:** For fetching historical trades beyond the limit, see the [Aggregate Trades List](./agg-trades.md) endpoint (if created) or the specific documentation for historical data retrieval methods. 