# Options Market Data: Order Book

Gets the order book depth for a specific Options symbol.

**Base URL:** `eapi.binance.com`

## Get Order Book Depth

`GET /eapi/v1/depth`

**Weight based on limit:**

| Limit         | Weight |
|---------------|--------|
| 5, 10, 20, 50 | 2      |
| 100           | 5      |
| 500           | 10     |
| 1000          | 20     |

**Parameters:**

| Name   | Type   | Mandatory | Description                                                        |
| ------ | ------ | --------- | ------------------------------------------------------------------ |
| symbol | STRING | YES       | Option trading pair, e.g., `BTC-200730-9000-C`                     |
| limit  | INT    | NO        | Default 100, Max 1000. Valid limits: `10`, `20`, `50`, `100`, `500`, `1000` |

**Response Example:**

```json
{
  "T": 1589436922972,   // Transaction time (ms)
  "u": 37461,           // Update ID
  "bids": [             // Buy orders (Price, Quantity)
    [
      "1000",
      "0.9"
    ]
  ],
  "asks": [              // Sell orders (Price, Quantity)
    [
      "1100",
      "0.1"
    ]
  ]
}
``` 