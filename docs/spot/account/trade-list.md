# Get Account Trade List (Spot)

Retrieves trades made by the account for a specific symbol on the Spot market.

## Endpoint

*   **`GET /api/v3/myTrades`** (Verify exact endpoint in official Spot API docs)

## Base URLs

*   `https://api.binance.com` (Primary)
*   `https://api1.binance.com`
*   `https://api2.binance.com`
*   `https://api3.binance.com`
*   `https://api4.binance.com`

## Security Type

*   **`USER_DATA`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Spot documentation)*

*   **`symbol`** (Mandatory): The symbol to get trades for (e.g., `BTCUSDT`).
*   **`orderId`** (Optional): If provided, trades related to this order ID will be returned.
*   **`startTime`** (Optional): Timestamp in milliseconds to get trades from.
*   **`endTime`** (Optional): Timestamp in milliseconds to get trades until.
*   **`fromId`** (Optional): Trade ID to fetch from. Default gets most recent trades.
*   **`limit`** (Optional): Default 500; max 1000.
*   **`recvWindow`** (Optional): The time window (in milliseconds) during which the request is valid (max typically 60000ms).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature of all parameters.

## Response Payload

Returns an array of trade detail objects.

*(Conceptual structure - check official docs for exact fields)*

```json
// Example Response (Conceptual)
[
  {
    "symbol": "BTCUSDT",
    "id": 28457, // Trade ID
    "orderId": 100234, // Order ID
    "orderListId": -1, // OCO order ID 
    "price": "4.00000100",
    "qty": "12.00000000",
    "quoteQty": "48.000012",
    "commission": "0.00001200",
    "commissionAsset": "BTC",
    "time": 1499865549590,
    "isBuyer": true,
    "isMaker": false,
    "isBestMatch": true
  },
  // ... more trades
]
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   If `fromId` is not set, the most recent trades are returned.
*   If `startTime` and `endTime` are defined, the results might be limited by the time range. Check documentation for interaction with `limit` and `fromId`.
*   Fetching trades can return a large dataset; use parameters like `startTime`, `endTime`, `fromId`, and `limit` to paginate or filter results. 