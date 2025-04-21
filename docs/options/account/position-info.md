# Options API - Position Information

This document describes how to query position information for your Options account.

**Base URL:** `https://eapi.binance.com`

## Endpoint: Get Position Information

*(Specific endpoint details, such as the exact path, method (e.g., GET), required parameters, and response structure, are not available in the provided documentation snippets. Please refer to the official Binance API documentation for the most up-to-date information.)*

**Authentication:** Requires API Key and Signature.

**Potential Parameters:**
*   Likely requires `symbol` or `underlying` to specify the options contract(s).
*   May require `timestamp` and `signature`.

**Typical Response Fields:**
*   `symbol`: The option symbol.
*   `positionAmt`: The quantity of contracts held.
*   `entryPrice`: The average entry price.
*   `markPrice`: The current mark price.
*   `unRealizedProfit`: Unrealized profit and loss (PNL).
*   `liquidationPrice`: The estimated liquidation price.
*   `leverage`: The leverage used for the position.
*   `marginType`: Isolated or Cross margin.
*   `isolatedMargin`: Margin allocated if isolated.

**Error Codes:**
*   Refer to the general [Error Codes](./../../error-codes.md) section. Specific errors related to invalid symbols or authentication issues might apply. 