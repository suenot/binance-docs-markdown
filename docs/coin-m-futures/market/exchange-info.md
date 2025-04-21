# Get Exchange Information (COIN-M Futures)

Retrieves current exchange trading rules, symbol information, and rate limits for the COIN-M Futures market.

## Endpoint

*   **`GET /dapi/v1/exchangeInfo`** (Verify endpoint in official COIN-M API docs)

## Base URL

*   `https://dapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required)

## Parameters

*   None

## Response Payload

The response contains server time, rate limits, and detailed information for each symbol.

*(Conceptual structure - check official docs for exact fields, types, and enums)*

```json
// Example Response (Conceptual)
{
  "timezone": "UTC",
  "serverTime": 1591702613943,
  "rateLimits": [
    // Rate limit objects (request type, interval, limit)
    {
      "rateLimitType": "REQUEST_WEIGHT",
      "interval": "MINUTE",
      "intervalNum": 1,
      "limit": 1200
    },
    // ... other rate limits (e.g., ORDERS)
  ],
  "exchangeFilters": [], // Global exchange filters (currently empty)
  "symbols": [
    {
      "symbol": "BTCUSD_PERP", 
      "pair": "BTCUSD",
      "contractType": "PERPETUAL", // e.g., PERPETUAL, CURRENT_QUARTER, NEXT_QUARTER
      "deliveryDate": 0, // Timestamp for delivery contracts
      "onboardDate": 1591702613943, // Timestamp when the contract went live
      "status": "TRADING",
      "maintMarginPercent": "2.5000", // Maintenance margin percent
      "requiredMarginPercent": "5.0000", // Required margin percent
      "baseAsset": "BTC",
      "quoteAsset": "USD",
      "marginAsset": "BTC", // Asset used for margin
      "pricePrecision": 1, // Decimal places for price
      "quantityPrecision": 0, // Decimal places for quantity (contracts)
      "baseAssetPrecision": 8,
      "quotePrecision": 8,
      "underlyingType": "COIN",
      "underlyingSubType": [],
      "settlePlan": 0,
      "triggerProtect": "0.0500", // Stop price protection threshold
      "liquidationFee": "0.010000", // Liquidation fee rate (added 2021-07-06)
      "marketTakeBound": "0.05", // Max price deviation for market orders (added 2021-07-06)
      "orderTypes": [
        "LIMIT",
        "MARKET",
        "STOP",
        "STOP_MARKET",
        "TAKE_PROFIT",
        "TAKE_PROFIT_MARKET",
        "TRAILING_STOP_MARKET"
      ],
      "timeInForce": [
        "GTC", // Good Til Canceled
        "IOC", // Immediate Or Cancel
        "FOK", // Fill Or Kill
        "GTX"  // Good Til Crossing (Post Only)
      ],
      "filters": [
        // Array of filter objects
        {
          "filterType": "PRICE_FILTER",
          "maxPrice": "100000",
          "minPrice": "0.1",
          "tickSize": "0.1"
        },
        {
          "filterType": "LOT_SIZE", // For contracts
          "maxQty": "1000",
          "minQty": "1",
          "stepSize": "1" 
        },
        {
          "filterType": "MARKET_LOT_SIZE",
          "maxQty": "1000",
          "minQty": "1",
          "stepSize": "1"
        },
        {
          "filterType": "MAX_NUM_ORDERS",
          "limit": 200
        },
        {
          "filterType": "MAX_NUM_ALGO_ORDERS",
          "limit": 100
        },
        {
          "filterType": "MIN_NOTIONAL",
          "notional": "1.0" // Minimum order value in quote asset (Added ~2021-01-21)
        },
        {
          "filterType": "PERCENT_PRICE",
          "multiplierUp": "1.05",
          "multiplierDown": "0.95",
          "multiplierDecimal": 4
        }
      ]
    },
    // ... other symbols (e.g., BTCUSD_241227)
  ]
}
```

**Important:**
*   This endpoint provides critical information for placing valid orders.
*   **Filters** define the rules for price (`PRICE_FILTER`), quantity (`LOT_SIZE`, `MARKET_LOT_SIZE`), minimum order value (`MIN_NOTIONAL`), and price deviation (`PERCENT_PRICE`). Orders violating these filters will be rejected.
*   `contractType`, `deliveryDate`, and `onboardDate` help distinguish between perpetual swaps and fixed-delivery futures.
*   `marginAsset` indicates which coin is used for margin and PnL calculation for that contract.
*   The `rateLimits` array should be checked to understand API request limits.
*   It is recommended to query this endpoint periodically (e.g., once a day) and cache the results, as trading rules and symbols can change. 