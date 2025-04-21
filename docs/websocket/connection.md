# Connecting to Binance WebSocket Streams

Binance provides WebSocket streams for receiving real-time market data and user account updates.

## Base URLs

Binance uses different base URLs for WebSocket streams depending on the market:

*   **Spot:** `wss://stream.binance.com:9443/ws` or `wss://stream.binance.com:443/ws`
*   **USDⓈ-M Futures:** `wss://fstream.binance.com/ws`
*   **COIN-M Futures:** `wss://dstream.binance.com/ws`
*   **Options:** (Verify official URL - often `wss://vstream.binance.com/ws`)

*Note: Combined streams might use `/stream` path instead of `/ws`.* 

## Connection Lifecycle

1.  **Establish Connection:** Connect to the appropriate base URL using a standard WebSocket client library.
2.  **Subscribe to Streams:** Send subscription messages in JSON format to specify the data you want to receive (e.g., specific symbol tickers, order book updates, user data).
3.  **Receive Data:** Process incoming JSON messages from the stream.
4.  **Keepalive:** Respond to Ping frames sent by the server with Pong frames to keep the connection alive. Connections may be dropped if no Pong is received within a certain timeframe.
5.  **Unsubscribe/Disconnect:** Send unsubscribe messages or close the connection when finished.

## Authentication (Private Streams)

Streams providing private user data (like order updates, balance changes) require authentication. This typically involves obtaining a `listenKey` via a REST API request and including it in the WebSocket stream URL or subscription messages.

*   See relevant REST API documentation for obtaining a `listenKey` (e.g., Spot User Data Stream, Futures User Data Stream).

## Important Considerations

*   **Message Format:** All messages sent and received are typically JSON strings.
*   **Rate Limits:** There might be limits on the number of connections per IP or subscriptions per connection.
*   **Reconnection:** Implement robust reconnection logic to handle network interruptions or server-side disconnects.

Refer to the specific documentation pages for Spot, Futures, and Options streams for detailed subscription messages and data formats. 