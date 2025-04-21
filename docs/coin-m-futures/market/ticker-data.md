# Get Ticker Data (COIN-M Futures)

Binance provides several endpoints to retrieve ticker information for COIN-M Futures markets.

## Base URL

*   `https://dapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required for all ticker endpoints listed here)

--- 

## 24hr Ticker Price Change Statistics

Retrieves rolling window price change statistics.

*   **Endpoint:** `GET /dapi/v1/ticker/24hr` (Verify endpoint)
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSD_PERP`).
    *   `pair` (Optional): Specific pair (e.g., `BTCUSD`).
*   **Response:** Single object if `symbol`/`pair` is specified, array of objects otherwise.
    *   Includes fields like `symbol`, `pair`, `priceChange`, `priceChangePercent`, `weightedAvgPrice`, `lastPrice`, `lastQty`, `openPrice`, `highPrice`, `lowPrice`, `volume` (base asset), `quoteVolume`, `openTime`, `closeTime`, `firstId`, `lastId`, `count`.

--- 

## Symbol Price Ticker

Retrieves the latest price for a symbol or symbols.

*   **Endpoint:** `GET /dapi/v1/ticker/price` (Verify endpoint)
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSD_PERP`).
    *   `pair` (Optional): Specific pair (e.g., `BTCUSD`).
*   **Response:** Single object `{"symbol": "BTCUSD_PERP", "price": "60000.1", "time": 16...}` if `symbol`/`pair` is specified, array of objects otherwise.
    *   Note: The `time` field for transaction time was added in an update.

--- 

## Symbol Order Book Ticker

Retrieves the best price/qty on the order book for a symbol or symbols.

*   **Endpoint:** `GET /dapi/v1/ticker/bookTicker` (Verify endpoint)
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSD_PERP`).
    *   `pair` (Optional): Specific pair (e.g., `BTCUSD`).
*   **Response:** Single object if `symbol`/`pair` is specified, array of objects otherwise.
    *   Includes `symbol`, `pair`, `bidPrice`, `bidQty`, `askPrice`, `askQty`, `time`.
    *   Note: The `time` field and additional event time fields (`E`, `T`) were added in updates.

--- 

## Mark Price and Funding Rate

Retrieves mark price and funding rate for a specific symbol or all symbols.

*   **Endpoint:** `GET /dapi/v1/premiumIndex` (Verify endpoint)
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSD_PERP`).
    *   `pair` (Optional): Specific pair (e.g., `BTCUSD`).
*   **Response:** Single object if `symbol`/`pair` is specified, array of objects otherwise.
    *   For perpetual contracts, includes fields like `symbol`, `pair`, `markPrice`, `indexPrice`, `lastFundingRate`, `nextFundingTime`, and possibly `time`.
    *   For delivery contracts, the structure might differ, lacking funding-related fields.

**Note:**
*   Verify the exact endpoint paths, parameters, and whether `symbol` or `pair` parameters are used in the official documentation.
*   Ticker data can also be obtained via [WebSocket Streams](./../websocket/coin-m-futures.md) for real-time updates.
*   According to the change logs, some fields like `time` for transaction time in the response and event/transaction time in WebSocket streams were added in updates.
*   The `lastFundingRate` and `nextFundingTime` fields were added to the premiumIndex endpoint for perpetual futures contracts in August 2020. 