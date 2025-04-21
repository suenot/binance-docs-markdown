# Binance API Endpoints Overview

Binance provides different base API endpoints for its various services (Spot, Futures, Options, etc.). Choosing the correct endpoint is crucial for interacting with the desired market or functionality.

## Production Endpoints

### Spot Trading & General API

These endpoints are used for Spot trading, general account information, and certain cross-market data.

*   **Primary:** `https://api.binance.com`
*   **Alternatives (Potentially Higher Performance, Less Stability):**
    *   `https://api1.binance.com`
    *   `https://api2.binance.com`
    *   `https://api3.binance.com`
    *   `https://api4.binance.com`

### USDⓈ-Margined Futures

Used specifically for USDⓈ-M Futures trading.

*   **Base URL:** `https://fapi.binance.com`

### COIN-Margined Futures

Used specifically for COIN-M Futures trading.

*   **Base URL:** `https://dapi.binance.com`

### European Options

*(Note: The base URL for options needs verification, commonly `eapi.binance.com` but confirm with official docs)*

*   **Assumed Base URL:** `https://eapi.binance.com`

### Portfolio Margin

Used for Portfolio Margin account interactions.

*   **Base URL:** `https://papi.binance.com`

### Data-Specific Endpoint (Public Data)

This endpoint can be used for accessing specific public data endpoints (`NONE` security type) potentially with better performance or different rate limits.

*   **Base URL:** `https://data-api.binance.vision`
*   **Applicable Endpoints (Examples):**
    *   `/api/v3/aggTrades`
    *   `/api/v3/avgPrice`
    *   `/api/v3/depth`
    *   `/api/v3/exchangeInfo`
    *   `/api/v3/klines`
    *   `/api/v3/ping`
    *   `/api/v3/ticker`
    *   `/api/v3/ticker/24hr`
    *   `/api/v3/ticker/bookTicker`
    *   `/api/v3/ticker/price`
    *   `/api/v3/time`
    *   `/api/v3/trades`
    *   `/api/v3/uiKlines`

## Testnet Endpoints

Binance provides testnet environments for practicing and testing integrations without using real funds.

*   **Spot Testnet:** `https://testnet.binance.vision` (Needs verification)
*   **Futures Testnet (USDⓈ-M & COIN-M):** `https://testnet.binancefuture.com`

**Important:** Always ensure you are using the correct base URL for the specific API call you intend to make. Mixing endpoints (e.g., using `fapi` for a spot order) will result in errors. 