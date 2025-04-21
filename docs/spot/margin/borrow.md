# Margin Borrow (Spot)

Initiates a borrow transaction in the Spot Margin account.

## Endpoint

*   **`POST /sapi/v1/margin/loan`** (Verify exact endpoint in official Margin API docs)

## Base URLs

*   *(Likely `https://api.binance.com` and alternatives, but verify - SAPI endpoints might have different base URLs or restrictions)*
*   `https://api.binance.com` (Primary Assumption)

## Security Type

*   **`MARGIN`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Margin documentation)*

*   **`asset`** (Mandatory): The asset to borrow (e.g., `USDT`, `BTC`).
*   **`isIsolated`** (Optional): Set to `TRUE` for isolated margin, `FALSE` for cross margin (Default: `FALSE` - verify).
*   **`symbol`** (Required if `isIsolated`=`TRUE`): Symbol for isolated margin (e.g., `BTCUSDT`).
*   **`amount`** (Mandatory): The amount to borrow.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Successful borrow typically returns a transaction ID.

*(Conceptual structure - check official docs)*

```json
// Example Response (Conceptual)
{
  "tranId": 100000001 
}
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   Ensure the account has sufficient collateral and borrowing is enabled.
*   Check margin account details (limits, interest rates) before borrowing. 