# Binance API Error Handling

Understanding how the Binance API signals errors is crucial for building robust applications.

## Error Payload

When an API request fails, Binance typically returns a JSON payload containing an error code and a descriptive message.

**Standard Error Format:**

```json
{
  "code": -1121,
  "msg": "Invalid symbol."
}
```

*   `code`: A specific Binance error code number (usually negative).
*   `msg`: A human-readable string explaining the error.

*Note: While this is the common format, some specific errors or API sections might have slightly different structures. Always check the response body.* 

## HTTP Status Codes

The API also uses standard HTTP status codes to indicate the general outcome of a request.

### Client Errors (`4XX`)

These indicate an issue with the request sent by your application.

*   **`400 Bad Request`**: General catch-all for malformed requests (e.g., invalid parameters, incorrect format). Check the error message (`msg`) for details.
*   **`401 Unauthorized`**: Missing or invalid API Key / Signature.
*   **`403 Forbidden`**: Indicates a WAF (Web Application Firewall) limit has been violated, or insufficient permissions for the requested operation.
*   **`408 Request Timeout`** (Futures/Portfolio Margin): Timeout occurred while waiting for a response from the backend server.
*   **`409 Conflict`** (Spot/Futures Data): Used when a `cancelReplace` order partially succeeds (e.g., cancellation fails, but placement succeeds). **Treat the execution status as UNKNOWN.**
*   **`418 I'm a teapot`** (Futures/Spot): IP address has been auto-banned due to repeatedly exceeding rate limits after receiving `429` codes.
*   **`429 Too Many Requests`**: Request rate limit violation.

### Server Errors (`5XX`)

These indicate an issue on Binance's side.

*   **`500 Internal Server Error`**: Generic internal error. The execution status is **UNKNOWN** and could have been a success. It's often recommended to retry later, especially if the message is generic like "Request occur unknown error."
*   **`503 Service Unavailable`**: Indicates the service is temporarily unavailable or the request timed out internally.
    *   If `msg` is "Unknown error, please check your request or try again later.", the API sent the request but didn't get a timely response. The execution status is **UNKNOWN**.
    *   If `msg` is "Service Unavailable.", the operation definitely failed. Retry later.
    *   If `msg` is "Internal error; unable to process your request. Please try again.", the operation failed. You can resend if necessary.

**Important:** For `409` and `5XX` errors, especially `500` and `503` (with certain messages), the status of your requested operation (like placing an order) might be **UNKNOWN**. Your application should have logic to re-query the status of the order/operation to determine the final outcome rather than assuming failure.

Refer to the official Binance documentation for a comprehensive list of specific `code` values and their meanings for each API. 