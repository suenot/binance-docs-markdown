# Binance COIN-M Futures WebSocket Streams

This page describes the WebSocket streams specific to the Binance COIN-Margined Futures market.

## Base URL

*   `wss://dstream.binance.com/ws`
*   For combined streams: `wss://dstream.binance.com/stream`

## Public Market Streams

These streams provide real-time market data for COIN-M Futures and do not require authentication.

*(Details about specific streams like Aggregate Trade, Index Price, Mark Price, Kline/Candlestick, Continuous Contract Kline, Index Price Kline, Mark Price Kline, Ticker, Book Ticker, Liquidation Order, Depth etc., including subscription messages and payload formats, will be added here based on official documentation.)*

**Example Subscription (Conceptual):**

```json
{
  "method": "SUBSCRIBE",
  "params": [
    "btcusd_perp@aggTrade",
    "btcusd_perp@markPrice@1s"
  ],
  "id": 1
}
```

## Private User Data Streams

These streams provide real-time updates on user account and trading activity for COIN-M Futures, such as order updates, account balance changes (including margin calls), and position updates. They require authentication using a `listenKey` obtained via the COIN-M Futures REST API.

*(Details about obtaining a COIN-M Futures listenKey and specific user data stream payloads (e.g., `ACCOUNT_CONFIG_UPDATE`, `ACCOUNT_UPDATE`, `ORDER_TRADE_UPDATE`) will be added here based on official documentation.)*

**Example Connection URL (Conceptual):**

`wss://dstream.binance.com/ws/<listenKey>`

**Note:** Refer to the [Connection](./connection.md) page for general WebSocket principles and the official Binance COIN-M Futures WebSocket documentation for definitive stream names, parameters, and payload structures. 