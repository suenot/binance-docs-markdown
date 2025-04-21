# Binance API Rate Limits

Binance APIs enforce rate limits to ensure fair usage and stability for all users. Exceeding these limits will result in temporary blocking.

## Understanding Rate Limits

*   **Types:** Rate limits are typically based on the number of requests per minute, per IP address, and sometimes per account or specific endpoint.
*   **Weights:** Different endpoints may have different "weights", contributing differently to the overall limit.
*   **Headers:** API responses often include headers (like `X-MBX-USED-WEIGHT-(intervalNum)(intervalLetter)`, `X-MBX-ORDER-COUNT-(intervalNum)(intervalLetter)`) indicating the current usage against the limits. Monitoring these headers is crucial for avoiding being blocked.
*   **Official Docs:** The specific limits and weighting systems vary across different API services (Spot, Futures, etc.) and can change. **Always refer to the official Binance API documentation for the most up-to-date and detailed rate limit information.**

## Handling Rate Limit Errors

*   **`HTTP 429 Too Many Requests`:** This status code indicates you have exceeded a rate limit.
    *   **Action:** Stop sending requests immediately. Check the `Retry-After` header (if provided) or implement an exponential backoff strategy before retrying.
*   **`HTTP 418 I'm a teapot`:** This status code means your IP address has been **auto-banned** because you continued sending requests after receiving `429` errors.
    *   **Action:** Stop sending requests immediately. The ban duration is usually specified in the error message or lasts for a significant period (minutes to hours). Review your code to ensure proper handling of `429` errors and implement rate limiting logic.

## Best Practices

*   **Monitor Headers:** Actively check the rate limit headers in responses.
*   **Implement Backoff:** Use exponential backoff when receiving `429` errors.
*   **Optimize Calls:** Combine requests where possible (e.g., fetching multiple tickers) and avoid polling excessively.
*   **Use WebSockets:** For real-time data, prefer WebSocket streams over polling REST endpoints.
*   **Distribute Load:** If necessary, use multiple IP addresses or API keys (within Binance's terms of service). 