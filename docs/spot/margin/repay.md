# Margin Repay (Spot)

Repays a loan in the Spot Margin account.

## Endpoint

*   **`POST /sapi/v1/margin/repay`** (Verify exact endpoint in official Margin API docs)

## Base URLs

*   *(Likely `https://api.binance.com` and alternatives, but verify - SAPI endpoints might have different base URLs or restrictions)*
*   `https://api.binance.com` (Primary Assumption)

## Security Type

*   **`MARGIN`** (Requires API Key and Signature)

## Parameters

*(Note: Verify exact mandatory/optional parameters in official Margin documentation)*

*   **`asset`** (Mandatory): The asset to repay (e.g., `USDT`, `BTC`).
*   **`isIsolated`** (Optional): Set to `TRUE` for isolated margin, `FALSE` for cross margin (Default: `FALSE` - verify).
*   **`symbol`** (Required if `isIsolated`=`TRUE`): Symbol for isolated margin (e.g., `BTCUSDT`).
*   **`amount`** (Mandatory): The amount to repay.
*   **`recvWindow`** (Optional): Time window (milliseconds).
*   **`timestamp`** (Mandatory): Request timestamp in milliseconds.
*   **`signature`** (Mandatory): HMAC SHA256 signature.

## Response Payload

Successful repayment typically returns a transaction ID.

*(Conceptual structure - check official docs)*

```json
// Example Response (Conceptual)
{
  "tranId": 100000002
}
```

**Important:**
*   Ensure correct [Authentication](./../../authentication.md).
*   Ensure the account has sufficient funds of the borrowed asset to perform the repayment. 