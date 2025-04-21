# Binance Options WebSocket Streams

This page outlines the WebSocket streams available for the Binance Options market.

## Base URL

*   **(Verify official URL - often `wss://vstream.binance.com/ws`)**

## Public Market Streams

These streams provide real-time market data for Options and typically do not require authentication.

*(Details about specific streams like Ticker, Kline, Trade, Depth etc., including subscription messages and payload formats, will be added here based on official documentation.)*

**Example Subscription (Conceptual):**

```json
{
  "method": "SUBSCRIBE",
  "params": [
    "BTC-241227-100000-C@ticker"
  ],
  "id": 1
}
```

## Private User Data Streams

These streams provide real-time updates on user account and trading activity for Options. They likely require authentication using a `listenKey` obtained via the Options REST API (verify endpoint).

*(Details about obtaining an Options listenKey and specific user data stream payloads will be added here based on official documentation.)*

**Example Connection URL (Conceptual - needs verification):**

`wss://vstream.binance.com/ws/<listenKey>`

**Note:** Refer to the [Connection](./connection.md) page for general WebSocket principles and the official Binance Options WebSocket documentation for definitive stream names, parameters, and payload structures. The exact base URLs and stream details for Options should be carefully verified. 