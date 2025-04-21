# Change Initial Leverage (USDⓈ-M Futures)

Changes the initial leverage for a specific symbol in the USDⓈ-M Futures market.

## Endpoint

*   **`POST /fapi/v1/leverage`** (Verify endpoint in official Futures API docs)

## Base URL

*   `https://fapi.binance.com`

## Security Type

*   **`TRADE`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters and constraints in official Futures documentation)*

*   **`symbol`** (Mandatory): The trading symbol (e.g., `BTCUSDT`).
*   **`leverage`** (Mandatory): Target initial leverage. Integer between 1 and the maximum allowed for the symbol (check `/fapi/v1/leverageBracket` or Exchange Info).
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Successful request returns the details of the new leverage setting.

*(Conceptual structure - check official docs for exact fields)*

```json
// Example Response (Conceptual)
{
  "leverage": 20, 
  "maxNotionalValue": "1000000", // Max notional value allowed for this leverage
  "symbol": "BTCUSDT"
}
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   The leverage must be within the allowed range for the specific symbol. Use the `GET /fapi/v1/leverageBracket` endpoint (which requires `USER_DATA` auth as per Change Log 2020-05-06) or check [Exchange Info](./../market/exchange-info.md) to find the valid leverage tiers and corresponding maximum notional values.
*   Changing leverage might fail if the new leverage is invalid or if the change would immediately cause margin issues with existing positions or open orders.
*   This sets the *initial* leverage. The *effective* leverage depends on the position size relative to the margin used.
*   Leverage changes might trigger the `ACCOUNT_CONFIG_UPDATE` event on the [User Data WebSocket Stream](./../websocket/usds-m-futures.md) (See Change Log 2021-01-26). 