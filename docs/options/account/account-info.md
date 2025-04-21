---
title: Account Information (USER_DATA)
sidebar_label: Account Information
sidebar_position: 1
---

Get current account information.

**GET** `/eapi/v1/marginAccount`

**Weight:** `3`

**Parameters:**

| Name       | Type | Mandatory | Description |
|------------|------|-----------|-------------|
| recvWindow | LONG | NO        | The value cannot be greater than 60000 |
| timestamp  | LONG | YES       |             |

**Response:**

```json
{
  "asset": [                  
    {
      "asset": "USDT",                  // Asset type
      "marginBalance": "10099.448",      // Account balance
      "equity": "10094.44662",          // Account equity
      "available": "8725.92524",        // Available funds
      "initialMargin": "1084.52138",    // Initial margin
      "maintMargin": "151.00138",       // Maintenance margin
      "unrealizedPNL": "-5.00138",      // Unrealized profit/loss
      "lpProfit": "-5.00138"           // Unrealized profit for long position 
    }
  ], 
  "greek": [
    {
      "underlying":"BTCUSDT",            // Option Underlying
      "delta": "-0.05",                  // Account delta
      "gamma": "-0.002",                 // Account gamma
      "theta": "-0.05",                  // Account theta
      "vega": "-0.002"                  // Account vega  
    }
  ],
  "time": 1592449455993                 // Time  
}  
``` 