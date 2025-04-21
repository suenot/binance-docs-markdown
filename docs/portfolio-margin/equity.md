# Portfolio Margin API - Account Equity

This document provides information on querying the overall equity of your Portfolio Margin account.

**Base URL:** `https://papi.binance.com`

## Endpoint: Get Account Equity

*(Specific endpoint details for fetching account equity, such as the exact path, method (e.g., GET), parameters, and response structure, are not explicitly detailed in the provided documentation snippets. Equity is often part of a broader account information or balance endpoint.)*

**Authentication:** Requires API Key and Signature.

**Potential Parameters:**
*   Standard parameters like `timestamp` and `signature` are usually required.

**Typical Response Fields:**
*   `accountEquity`: The total value of the account, often calculated in a base currency (e.g., USD, BTC). This usually includes wallet balances plus unrealized PNL from open positions.
*   `marginBalance`: The balance used for margin calculations.
*   `initialMargin`: The total initial margin required for open positions.
*   `maintenanceMargin`: The total maintenance margin required for open positions.
*   `unrealizedPNL`: Total unrealized profit and loss across all positions.
*   `marginLevel` or `riskRatio`: A measure of the account's risk, often calculated as `accountEquity / maintenanceMargin` or similar.

**General API Information:**
*   Endpoints return JSON objects or raw primitives.
*   Timestamps are in UTC milliseconds.
*   Refer to [General Info](./account-info.md) for details on request parameters and error handling.

**Note:** Account equity calculations in Portfolio Margin can be complex, considering the combined risk of spot, margin, futures, and potentially options positions, netted across different assets used as collateral. The specific calculation method might be detailed in the official API documentation. 