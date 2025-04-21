# Get Order Book Depth (COIN-M Futures)

Retrieves the order book (bids and asks) for a specific symbol on the COIN-M Futures market.

## Endpoint

*   **`GET /dapi/v1/depth`** (Verify endpoint in official COIN-M API docs)

## Base URL

*   `https://dapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSD_PERP`, `ETHUSD_241227`).
*   **`limit`** (Optional): Default 100. Valid limits: [5, 10, 20, 50, 100, 500, 1000].

## Response Payload

The response contains the last update ID, transaction time, event time, and arrays for bids and asks.

*   `lastUpdateId`: The ID of the last update included in this snapshot.
*   `T`: Transaction time (milliseconds).
*   `E`: Message output time (event time, milliseconds).
*   `bids`: Array of bid entries.
    *   Each entry is `[price, quantity]`. Quantity is in contracts.
    *   Bids are sorted in descending order by price (highest bid first).
*   `asks`: Array of ask entries.
    *   Each entry is `[price, quantity]`. Quantity is in contracts.
    *   Asks are sorted in ascending order by price (lowest ask first).

```json
// Example Response (Conceptual - BTCUSD_PERP)
{
  "lastUpdateId": 123456789,
  "E": 1591702614000,
  "T": 1591702613950,
  "bids": [
    ["9000.1", "150"], // Price (USD), Quantity (Contracts)
    ["9000.0", "200"],
    // ...
  ],
  "asks": [
    ["9000.2", "120"],
    ["9000.3", "80"],
    // ...
  ]
}
```

**Important:**
*   This provides a snapshot of the order book. For real-time updates and maintaining a local order book, use the [Depth WebSocket Stream](./../websocket/coin-m-futures.md) and follow the official guidelines on [How to manage a local order book correctly](https://developers.binance.com/docs/derivatives/coin-margined-futures/websocket-market-streams/How-to-manage-a-local-order-book-correctly).
*   The quantity is expressed in number of contracts. 