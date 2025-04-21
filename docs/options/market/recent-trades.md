# Options Market Data: Recent Trades List

Gets the most recent market trades for a specific Options symbol.

**Base URL:** `eapi.binance.com`

## Get Recent Trades

`GET /eapi/v1/trades`

**Weight:** 5

**Parameters:**

| Name   | Type   | Mandatory | Description                                     |
| ------ | ------ | --------- | ----------------------------------------------- |
| symbol | STRING | YES       | Option trading pair, e.g., `BTC-200730-9000-C`  |
| limit  | INT    | NO        | Default 100, Max 500. Number of trades to return. |

**Response Example:**

```json
[
  {
    "id": "1",             // Trade ID
    "symbol": "BTC-220722-19000-C",
    "price": "1000",      // Price
    "qty": "-0.1",        // Quantity
    "quoteQty": "-100",   // Quote asset quantity
    "side": -1,           // -1 for Sell, 1 for Buy
    "time": 1592449455993 // Trade execution time (ms)
  }
]
``` 