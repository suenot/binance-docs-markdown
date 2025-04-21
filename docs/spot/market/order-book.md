# Get Order Book Depth (Spot)

This endpoint retrieves the order book (bids and asks) for a specific symbol on the Spot market.

## Endpoint

*   **`GET /api/v3/depth`**

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
*   **`limit`** (Optional): Default 100; max 5000. Valid limits: [5, 10, 20, 50, 100, 500, 1000, 5000].

## Response Payload

The response contains the last update ID and arrays for bids and asks.

*   `lastUpdateId`: The ID of the last update included in this snapshot.
*   `bids`: Array of bid entries.
    *   Each entry is `[price, quantity]`.
    *   Bids are sorted in descending order by price (highest bid first).
*   `asks`: Array of ask entries.
    *   Each entry is `[price, quantity]`.
    *   Asks are sorted in ascending order by price (lowest ask first).

```json
// Example Response (BTCUSDT, limit=5)
{
  "lastUpdateId": 1027024,
  "bids": [
    ["4.00000000", "431.00000000"],
    ["3.99900000", "212.00000000"],
    ["3.99800000", "50.00000000"],
    ["3.99700000", "100.00000000"],
    ["3.99600000", "25.00000000"]
  ],
  "asks": [
    ["4.00100000", "120.00000000"],
    ["4.00200000", "55.00000000"],
    ["4.00300000", "301.00000000"],
    ["4.00400000", "87.00000000"],
    ["4.00500000", "99.00000000"]
  ]
}
```

**Note:** For real-time order book updates, consider using the [Depth WebSocket Stream](./../websocket/spot.md). 