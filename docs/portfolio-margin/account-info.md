# Portfolio Margin API - Account Information

This document covers retrieving general account information using the Portfolio Margin API.

**Base URL:** `https://papi.binance.com`

## General API Information

*   All endpoints return either a JSON object or a raw primitive.
*   Data is returned in ascending order (oldest first, newest last).
*   All time and timestamp related fields are in UTC milliseconds.
*   All data types adopt definitions from JAVA.

## Endpoint: Get Account Information

*(Specific endpoint details for fetching general account information, such as the exact path, method, parameters, and response structure, are not explicitly detailed in the provided documentation snippets. However, endpoints typically exist to query overall account status, margin levels, and asset details.)*

**Authentication:** Requires API Key and Signature (HMAC SHA256, potentially using RSA as shown in one example snippet for placing orders).

**Potential Parameters:**
*   Standard parameters like `timestamp` and `signature` are usually required.
*   Optional parameters might filter results or specify details needed.

**Typical Response Fields:**
*   Account status (e.g., margin level, risk ratio)
*   Permissions (e.g., trading enabled)
*   Asset balances (detailed in the [Balance](./balance.md) section)
*   Account equity (detailed in the [Equity](./equity.md) section)

**Request Parameters:**
*   Parameters can be sent in the `query string` or in the `request body` with content type `application/x-www-form-urlencoded`.
*   You may mix parameters between both the query string and request body.
*   If a parameter is sent in both the query string and request body, the `query string` parameter will be used.

**Error Handling:**
*   Refer to the general [Error Codes](./../error-codes.md) section.
*   Specific errors related to Portfolio Margin might apply (e.g., insufficient margin).
*   HTTP `4XX` codes are used for client-side errors.
*   HTTP `503` indicates potential service unavailability or timeouts where the execution status is UNKNOWN.

**Recent Relevant Updates (from Changelog):**
*   `GET /papi/v1/portfolio/negative-balance-exchange-record` (2025-01-20): Query user negative balance auto-exchange record.
*   `GET papi/v1/rateLimit/order` (2025-01-06): Query user order rate limit. 