# Python SDKs / Connectors for Binance API

Binance and the community provide several Python libraries (often called connectors) to facilitate interaction with the various Binance APIs.

## Official Binance Connectors

Binance maintains lightweight official connectors designed to provide direct access to API endpoints.

*   **Spot API Connector:**
    *   GitHub: <https://github.com/binance/binance-connector-python>
    *   Focus: Spot trading, Wallet, Margin, and other related endpoints available via `api.binance.com`.

*   **Futures API Connector:**
    *   GitHub: <https://github.com/binance/binance-futures-connector-python>
    *   Focus: USDⓈ-M and COIN-M Futures trading endpoints available via `fapi.binance.com` and `dapi.binance.com`.

**Note:** These official connectors are generally lightweight wrappers around the REST API and WebSocket streams. You will likely need to handle rate limiting, error checking, and data processing yourself.

## Community Libraries

*(This section can be expanded later if popular community libraries are identified)*

There are also several popular third-party Python libraries for interacting with Binance. These often provide higher-level abstractions, built-in rate limiting handling, and other convenience features. Examples might include `python-binance`. Research and choose based on your project's needs and the library's maintenance status.

**Disclaimer:** When using third-party libraries, always review their security practices and ensure they are actively maintained. 