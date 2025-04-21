# Get Ticker Data (Spot)

Binance provides several endpoints to retrieve ticker information for Spot markets.

## Base URLs

*   `https://api.binance.com` (Primary)
*   `https://api1.binance.com`
*   `https://api2.binance.com`
*   `https://api3.binance.com`
*   `https://api4.binance.com`
*   `https://data-api.binance.vision` (Data-specific endpoint for all below)

## Security Type

*   **`NONE`** (No authentication required for all ticker endpoints listed here)

--- 

## 24hr Ticker Price Change Statistics

Retrieves rolling window price change statistics.

*   **Endpoint:** `GET /api/v3/ticker/24hr`
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSDT`).
    *   `symbols` (Optional): Array of symbols (URL-encoded JSON).
*   **Response:** Single object if `symbol` is specified, array of objects if `symbols` or no parameter is specified.
    *   Includes fields like `priceChange`, `priceChangePercent`, `weightedAvgPrice`, `lastPrice`, `highPrice`, `lowPrice`, `volume`, `quoteVolume`, `openTime`, `closeTime`, `firstId`, `lastId`, `count`.

--- 

## Symbol Price Ticker

Retrieves the latest price for a symbol or symbols.

*   **Endpoint:** `GET /api/v3/ticker/price`
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSDT`).
    *   `symbols` (Optional): Array of symbols (URL-encoded JSON).
*   **Response:** Single object `{"symbol": "BTCUSDT", "price": "60000.01"}` if `symbol` is specified, array of objects if `symbols` or no parameter is specified.

--- 

## Symbol Order Book Ticker

Retrieves the best price/qty on the order book for a symbol or symbols.

*   **Endpoint:** `GET /api/v3/ticker/bookTicker`
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSDT`).
    *   `symbols` (Optional): Array of symbols (URL-encoded JSON).
*   **Response:** Single object if `symbol` is specified, array of objects if `symbols` or no parameter is specified.
    *   Includes `symbol`, `bidPrice`, `bidQty`, `askPrice`, `askQty`.

--- 

## Generic Ticker (Potentially Deprecated/Less Common)

The snippets also mention `GET /api/v3/ticker`. Consult official documentation for its exact behavior, as `/24hr`, `/price`, and `/bookTicker` are more specific and commonly used.

**Note:** Ticker data can also be obtained via [WebSocket Streams](./../websocket/spot.md) for real-time updates. 