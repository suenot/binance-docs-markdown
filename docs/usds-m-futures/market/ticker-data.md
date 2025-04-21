# Get Ticker Data (USDⓈ-M Futures)

Binance provides several endpoints to retrieve ticker information for USDⓈ-M Futures markets.

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`NONE`** (No authentication required for all ticker endpoints listed here)

--- 

## 24hr Ticker Price Change Statistics

Retrieves rolling window price change statistics.

*   **Endpoint:** `GET /fapi/v1/ticker/24hr` (Verify endpoint)
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSDT`).
    *   `pair` (Optional): Specific pair (e.g., `BTCUSDT`). *(Check if `symbol` or `pair` is used)*
*   **Response:** Single object if `symbol`/`pair` is specified, array of objects otherwise.
    *   Includes fields like `symbol`, `priceChange`, `priceChangePercent`, `weightedAvgPrice`, `lastPrice`, `lastQty`, `openPrice`, `highPrice`, `lowPrice`, `volume` (base asset), `quoteVolume`, `openTime`, `closeTime`, `firstId`, `lastId`, `count`.

--- 

## Symbol Price Ticker

Retrieves the latest price for a symbol or symbols.

*   **Endpoint:** `GET /fapi/v1/ticker/price` (Verify endpoint)
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSDT`).
    *   `pair` (Optional): Specific pair (e.g., `BTCUSDT`). *(Check if `symbol` or `pair` is used)*
*   **Response:** Single object `{"symbol": "BTCUSDT", "price": "60000.01", "time": 16...}` if `symbol`/`pair` is specified, array of objects otherwise.

--- 

## Symbol Order Book Ticker

Retrieves the best price/qty on the order book for a symbol or symbols.

*   **Endpoint:** `GET /fapi/v1/ticker/bookTicker` (Verify endpoint)
*   **Parameters:**
    *   `symbol` (Optional): Specific symbol (e.g., `BTCUSDT`).
    *   `pair` (Optional): Specific pair (e.g., `BTCUSDT`). *(Check if `symbol` or `pair` is used)*
*   **Response:** Single object if `symbol`/`pair` is specified, array of objects otherwise.
    *   Includes `symbol`, `pair`, `bidPrice`, `bidQty`, `askPrice`, `askQty`, `time`.

**Note:**
*   Verify the exact endpoint paths and whether `symbol` or `pair` parameters are used in the official documentation.
*   Ticker data can also be obtained via [WebSocket Streams](./../websocket/usds-m-futures.md) for real-time updates. 