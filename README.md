# Binance API Documentation

This repository contains community-driven Markdown documentation for the Binance API, aiming for clarity and ease of use, especially for integration with AI systems.

## Getting Started
- [x] [Introduction](./docs/introduction.md) - General concepts, API types.
- [x] [Endpoints Overview](./docs/endpoints.md) - List of base URLs for different services.
- [x] [Authentication](./docs/authentication.md) - API Key, Secret Key, Signature generation (HMAC SHA256).
- [x] [Error Codes](./docs/error-codes.md) - Common error patterns and specific codes.
- [x] [Rate Limits](./docs/rate-limits.md) - Understanding and handling request limits.

## SDK Examples
*(Note: Links point to official/community resources where available)*
- [x] [Python SDK](./docs/sdk/python.md)
- [x] [Java SDK](./docs/sdk/java.md)
- [x] [Node.js SDK](./docs/sdk/nodejs.md)
- [x] [Go SDK](./docs/sdk/go.md)
- [x] [C# SDK](./docs/sdk/csharp.md)

## WebSocket Streams
- [x] [Connection](./docs/websocket/connection.md) - Establishing WebSocket connections.
- [x] [Spot Streams](./docs/websocket/spot.md) - Market data and account updates for Spot.
- [x] [USDⓈ-M Futures Streams](./docs/websocket/usds-m-futures.md) - Market data and account updates for USDⓈ-M Futures.
- [x] [COIN-M Futures Streams](./docs/websocket/coin-m-futures.md) - Market data and account updates for COIN-M Futures.
- [x] [Options Streams](./docs/websocket/options.md) - Market data and account updates for Options.

## Spot Trading (api.binance.com)
### REST API
- Market Data
  - [x] [Exchange Info](./docs/spot/market/exchange-info.md)
  - [x] [Order Book](./docs/spot/market/order-book.md)
  - [x] [Recent Trades](./docs/spot/market/recent-trades.md)
  - [x] [Candlestick (Kline) Data](./docs/spot/market/kline-data.md)
  - [x] [Ticker Data](./docs/spot/market/ticker-data.md)
- Trading
  - [x] [Place Order](./docs/spot/trade/place-order.md)
  - [x] [Cancel Order](./docs/spot/trade/cancel-order.md)
  - [x] [Query Order](./docs/spot/trade/query-order.md)
  - [x] [Current Open Orders](./docs/spot/trade/open-orders.md)
  - [x] [All Orders](./docs/spot/trade/all-orders.md)
- Account
  - [x] [Account Information](./docs/spot/account/account-info.md)
  - [x] [Account Trade List](./docs/spot/account/trade-list.md)
- Margin Trading
  - [x] [Borrow](./docs/spot/margin/borrow.md)
  - [x] [Repay](./docs/spot/margin/repay.md)
  - [x] [Margin Account Details](./docs/spot/margin/account-details.md)

## USDⓈ-Margined Futures Trading (fapi.binance.com)
### REST API
- Market Data
  - [x] [Exchange Info](./docs/usds-m-futures/market/exchange-info.md)
  - [x] [Order Book](./docs/usds-m-futures/market/order-book.md)
  - [x] [Recent Trades](./docs/usds-m-futures/market/recent-trades.md)
  - [x] [Kline Data](./docs/usds-m-futures/market/kline-data.md)
  - [x] [Ticker Data](./docs/usds-m-futures/market/ticker-data.md)
- Trading
  - [x] [Place Order](./docs/usds-m-futures/trade/place-order.md)
  - [x] [Cancel Order](./docs/usds-m-futures/trade/cancel-order.md)
  - [x] [Query Order](./docs/usds-m-futures/trade/query-order.md)
  - [x] [Open Orders](./docs/usds-m-futures/trade/open-orders.md)
  - [x] [All Orders](./docs/usds-m-futures/trade/all-orders.md)
- Account
  - [x] [Position Information](./docs/usds-m-futures/account/position-info.md)
  - [x] [Account Balance](./docs/usds-m-futures/account/balance.md)
  - [x] [Set Leverage](./docs/usds-m-futures/account/set-leverage.md)
  - [x] [Set Margin Type](./docs/usds-m-futures/account/set-margin-type.md)

## COIN-Margined Futures Trading (dapi.binance.com)
### REST API
- Market Data
  - [x] [Exchange Info](./docs/coin-m-futures/market/exchange-info.md)
  - [x] [Order Book](./docs/coin-m-futures/market/order-book.md)
  - [x] [Recent Trades](./docs/coin-m-futures/market/recent-trades.md)
  - [x] [Kline Data](./docs/coin-m-futures/market/kline-data.md)
  - [x] [Ticker Data](./docs/coin-m-futures/market/ticker-data.md)
- Trading
  - [x] [Place Order](./docs/coin-m-futures/trade/place-order.md)
  - [x] [Cancel Order](./docs/coin-m-futures/trade/cancel-order.md)
  - [x] [Cancel All Open Orders](./docs/coin-m-futures/trade/cancel-all-orders.md)
- Account
  - [x] [Position Information](./docs/coin-m-futures/account/position-info.md)
  - [x] [Account Balance](./docs/coin-m-futures/account/balance.md)
  - [x] [Set Leverage](./docs/coin-m-futures/account/set-leverage.md)
  - [x] [Set Margin Type](./docs/coin-m-futures/account/set-margin-type.md)

## Options Trading (eapi.binance.com)
### REST API
- Market Data
  - [x] [Exchange Info](./docs/options/market/exchange-info.md)
  - [x] [Order Book](./docs/options/market/order-book.md)
  - [x] [Recent Trades](./docs/options/market/recent-trades.md)
  - [x] [Ticker Data](./docs/options/market/ticker-data.md)
- Trading
  - [x] [Place Order](./docs/options/trade/place-order.md)
  - [x] [Cancel Order](./docs/options/trade/cancel-order.md)
  - [x] [Query Order](./docs/options/trade/query-order.md)
- Account
  - [x] [Account Information](./docs/options/account/account-info.md)
  - [x] [Position Information](./docs/options/account/position-info.md)

## Portfolio Margin (papi.binance.com)
- [x] [Account Information](./docs/portfolio-margin/account-info.md)
- [x] [Balance](./docs/portfolio-margin/balance.md)
- [x] [Account Equity](./docs/portfolio-margin/equity.md)

## Additional Resources
- [Official Binance API Documentation](https://developers.binance.com/en)
- [Binance API Status](https://www.binance.com/en/network)
- [Binance Developer Community](https://dev.binance.vision/)
- [Futures Testnet](https://testnet.binancefuture.com/)