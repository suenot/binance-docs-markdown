# Change Margin Type (USDⓈ-M Futures)

Changes the margin type (ISOLATED or CROSSED) for a specific symbol in the USDⓈ-M Futures market.

## Endpoint

*   **`POST /fapi/v1/marginType`** (Verify endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`TRADE`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Futures documentation)*

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSDT`).
*   **`marginType`** (Mandatory): `ISOLATED` or `CROSSED`.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Successful request returns a confirmation message.

*(Conceptual structure - based on COIN-M and Chinese USDⓈ-M docs)*

```json
// Example Response (Conceptual)
{
	"code": 200,
	"msg": "success"
}
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   Changing the margin type is only possible if the user has no open positions or open orders for the specified `symbol`.
*   In Hedge Mode, both LONG and SHORT positions for a symbol share the same margin type.
*   Changes in margin type might be reflected in the `ACCOUNT_UPDATE` event on the [User Data WebSocket Stream](./../websocket/usds-m-futures.md). 