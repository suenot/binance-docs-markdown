# Get Order Book Depth (USDⓈ-M Futures)

Retrieves the order book (bids and asks) for a specific symbol on the USDⓈ-M Futures market.

## Endpoint

*   **`GET /fapi/v1/depth`** (Verify exact endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSDT`).
*   **`limit`** (Optional): Default 500. Valid limits: [5, 10, 20, 50, 100, 500, 1000].

## Response Payload

The response contains the last update ID, transaction time, event time, and arrays for bids and asks.

*   `lastUpdateId`: The ID of the last update included in this snapshot.
*   `T`: Transaction time (milliseconds).
*   `E`: Message output time (event time, milliseconds).
*   `bids`: Array of bid entries.
    *   Each entry is `[price, quantity]`.
    *   Bids are sorted in descending order by price (highest bid first).
*   `asks`: Array of ask entries.
    *   Each entry is `[price, quantity]`.
    *   Asks are sorted in ascending order by price (lowest ask first).

```json
// Example Response (Conceptual)
{
  "lastUpdateId": 1027024,
  "E": 1589436922972,
  "T": 1589436922959,
  "bids": [
    ["9700.00", "431"], // Price, Quantity
    ["9699.99", "212"],
    // ...
  ],
  "asks": [
    ["9700.01", "120"],
    ["9700.02", "55"],
    // ...
  ]
}
```

**Note:** For real-time order book updates, consider using the [Depth WebSocket Stream](./../websocket/usds-m-futures.md). 