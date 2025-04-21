# Portfolio Margin API - Balance

This document describes how to query asset balances within your Portfolio Margin account.

**Base URL:** `https://papi.binance.com`

## Endpoint: Get Account Balance

*(Specific endpoint details for fetching account balances, such as the exact path, method (e.g., GET), parameters, and response structure, are not explicitly detailed in the provided documentation snippets. However, dedicated endpoints usually exist for this purpose.)*

**Authentication:** Requires API Key and Signature.

**Potential Parameters:**
*   Standard parameters like `timestamp` and `signature` are usually required.
*   May include optional parameters to filter by specific assets.

**Typical Response Structure:**
*   Often returns a list of assets held in the account.
*   Each asset entry typically includes:
    *   `asset`: The asset ticker (e.g., `BTC`, `USDT`).
    *   `walletBalance` or `totalBalance`: The total amount of the asset held.
    *   `availableBalance`: The amount available for withdrawal or trading (considering margin requirements).
    *   `crossWalletBalance`: Balance in the cross margin wallet (if applicable).
    *   `lockedBalance`: Amount locked in open orders or positions.

**General API Information:**
*   Endpoints return JSON objects or raw primitives.
*   Timestamps are in UTC milliseconds.
*   Refer to [General Info](./account-info.md) for details on request parameters and error handling.

**Recent Relevant Updates (from Changelog):**
*   `GET /sapi/v1/portfolio/earn-asset-balance` (2025-04-15): Query Unified Account LDUSDT transferable amount (Note: uses `sapi` base URL, likely related but distinct).
*   `GET /papi/v1/portfolio/negative-balance-exchange-record` (2025-01-20): Provides information about auto-exchanges due to negative balances, which relates to balance management. 