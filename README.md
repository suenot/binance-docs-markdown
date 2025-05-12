# Binance API Documentation
[![Context7 Docs](https://badgen.net/badge/Context7/Binance%20Docs/blue)](https://context7.com/suenot/binance-docs-markdown)

This repository contains community-driven Markdown documentation for the Binance API, aiming for clarity and ease of use, especially for integration with AI systems.

## Getting Started
- [Introduction](./docs/introduction.md) - General concepts, API types.
- [Endpoints Overview](./docs/endpoints.md) - List of base URLs for different services.
- [Authentication](./docs/authentication.md) - API Key, Secret Key, Signature generation (HMAC SHA256).
- [Error Codes](./docs/error-codes.md) - Common error patterns and specific codes.
- [Rate Limits](./docs/rate-limits.md) - Understanding and handling request limits.

## SDK Examples
*(Note: Links point to official/community resources where available)*
- [Python SDK](./docs/sdk/python.md)
- [Java SDK](./docs/sdk/java.md)
- [Node.js SDK](./docs/sdk/nodejs.md)
- [Go SDK](./docs/sdk/go.md)
- [C# SDK](./docs/sdk/csharp.md)

## WebSocket Streams
- [Connection](./docs/websocket/connection.md) - Establishing WebSocket connections.
- [Spot Streams](./docs/websocket/spot.md) - Market data and account updates for Spot.
- [USDⓈ-M Futures Streams](./docs/websocket/usds-m-futures.md) - Market data and account updates for USDⓈ-M Futures.
- [COIN-M Futures Streams](./docs/websocket/coin-m-futures.md) - Market data and account updates for COIN-M Futures.
- [Options Streams](./docs/websocket/options.md) - Market data and account updates for Options.

## Spot Trading (api.binance.com)
### REST API
- Market Data
  - [Exchange Info](./docs/spot/market/exchange-info.md)
  - [Order Book](./docs/spot/market/order-book.md)
  - [Recent Trades](./docs/spot/market/recent-trades.md)
  - [Candlestick (Kline) Data](./docs/spot/market/kline-data.md)
  - [Ticker Data](./docs/spot/market/ticker-data.md)
- Trading
  - [Place Order](./docs/spot/trade/place-order.md)
  - [Cancel Order](./docs/spot/trade/cancel-order.md)
  - [Query Order](./docs/spot/trade/query-order.md)
  - [Current Open Orders](./docs/spot/trade/open-orders.md)
  - [All Orders](./docs/spot/trade/all-orders.md)
- Account
  - [Account Information](./docs/spot/account/account-info.md)
  - [Account Trade List](./docs/spot/account/trade-list.md)
- Margin Trading
  - [Borrow](./docs/spot/margin/borrow.md)
  - [Repay](./docs/spot/margin/repay.md)
  - [Margin Account Details](./docs/spot/margin/account-details.md)

## USDⓈ-Margined Futures Trading (fapi.binance.com)
### REST API
- Market Data
  - [Exchange Info](./docs/usds-m-futures/market/exchange-info.md)
  - [Order Book](./docs/usds-m-futures/market/order-book.md)
  - [Recent Trades](./docs/usds-m-futures/market/recent-trades.md)
  - [Kline Data](./docs/usds-m-futures/market/kline-data.md)
  - [Ticker Data](./docs/usds-m-futures/market/ticker-data.md)
- Trading
  - [Place Order](./docs/usds-m-futures/trade/place-order.md)
  - [Cancel Order](./docs/usds-m-futures/trade/cancel-order.md)
  - [Query Order](./docs/usds-m-futures/trade/query-order.md)
  - [Open Orders](./docs/usds-m-futures/trade/open-orders.md)
  - [All Orders](./docs/usds-m-futures/trade/all-orders.md)
- Account
  - [Position Information](./docs/usds-m-futures/account/position-info.md)
  - [Account Balance](./docs/usds-m-futures/account/balance.md)
  - [Set Leverage](./docs/usds-m-futures/account/set-leverage.md)
  - [Set Margin Type](./docs/usds-m-futures/account/set-margin-type.md)

## COIN-Margined Futures Trading (dapi.binance.com)
### REST API
- Market Data
  - [Exchange Info](./docs/coin-m-futures/market/exchange-info.md)
  - [Order Book](./docs/coin-m-futures/market/order-book.md)
  - [Recent Trades](./docs/coin-m-futures/market/recent-trades.md)
  - [Kline Data](./docs/coin-m-futures/market/kline-data.md)
  - [Ticker Data](./docs/coin-m-futures/market/ticker-data.md)
- Trading
  - [Place Order](./docs/coin-m-futures/trade/place-order.md)
  - [Cancel Order](./docs/coin-m-futures/trade/cancel-order.md)
  - [Cancel All Open Orders](./docs/coin-m-futures/trade/cancel-all-orders.md)
- Account
  - [Position Information](./docs/coin-m-futures/account/position-info.md)
  - [Account Balance](./docs/coin-m-futures/account/balance.md)
  - [Set Leverage](./docs/coin-m-futures/account/set-leverage.md)
  - [Set Margin Type](./docs/coin-m-futures/account/set-margin-type.md)

## Options Trading (eapi.binance.com)
### REST API
- Market Data
  - [Exchange Info](./docs/options/market/exchange-info.md)
  - [Order Book](./docs/options/market/order-book.md)
  - [Recent Trades](./docs/options/market/recent-trades.md)
  - [Ticker Data](./docs/options/market/ticker-data.md)
- Trading
  - [Place Order](./docs/options/trade/place-order.md)
  - [Cancel Order](./docs/options/trade/cancel-order.md)
  - [Query Order](./docs/options/trade/query-order.md)
- Account
  - [Account Information](./docs/options/account/account-info.md)
  - [Position Information](./docs/options/account/position-info.md)

## Portfolio Margin (papi.binance.com)
- [Account Information](./docs/portfolio-margin/account-info.md)
- [Balance](./docs/portfolio-margin/balance.md)
- [Account Equity](./docs/portfolio-margin/equity.md)

## Additional Resources
- [Official Binance API Documentation](https://developers.binance.com/en)
- [Binance API Status](https://www.binance.com/en/network)
- [Binance Developer Community](https://dev.binance.vision/)
- [Futures Testnet](https://testnet.binancefuture.com/)
