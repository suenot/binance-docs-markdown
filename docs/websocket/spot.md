# Binance Spot WebSocket Streams

This page details the WebSocket streams available for the Binance Spot market.

## Base URL

*   `wss://stream.binance.com:9443/ws`
*   `wss://stream.binance.com:443/ws`
*   For combined streams: `wss://stream.binance.com:9443/stream` or `wss://stream.binance.com:443/stream`

## Public Market Streams

These streams provide real-time market data and do not require authentication.

*(Details about specific streams like Aggregate Trade, Trade, Kline/Candlestick, Ticker, Book Ticker, Depth etc., including subscription messages and payload formats, will be added here based on official documentation.)*

**Example Subscription (Conceptual):**

```json
{
  "method": "SUBSCRIBE",
  "params": [
    "btcusdt@aggTrade",
    "btcusdt@depth"
  ],
  "id": 1
}
```

## Private User Data Streams

These streams provide real-time updates on user account activity, such as order updates, account balance changes, etc. They require authentication using a `listenKey` obtained via the REST API.

*(Details about obtaining a listenKey and specific user data stream payloads will be added here based on official documentation.)*

**Example Connection URL (Conceptual):**

`wss://stream.binance.com:9443/ws/<listenKey>`

**Note:** Refer to the [Connection](./connection.md) page for general WebSocket principles and the official Binance Spot WebSocket documentation for definitive stream names, parameters, and payload structures. 