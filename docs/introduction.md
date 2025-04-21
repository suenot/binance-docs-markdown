# Introduction to the Binance API

Welcome to the Binance API documentation. This guide provides an overview of the Binance API ecosystem, helping you get started with programmatic access to the world's leading cryptocurrency exchange.

## Overview

Binance offers a comprehensive suite of APIs enabling developers to interact with various platform features, including:

*   **Spot Trading:** Buying and selling cryptocurrencies at current market prices.
*   **Margin Trading:** Trading with borrowed funds.
*   **USDⓈ-Margined Futures:** Trading futures contracts settled in stablecoins (like USDT, BUSD).
*   **COIN-Margined Futures:** Trading futures contracts settled in the base cryptocurrency (like BTC, ETH).
*   **Options Trading:** Trading European-style vanilla options.
*   **Portfolio Margin:** Managing risk across different asset classes under a unified account.
*   **Wallet Management:** Accessing account balances, deposit/withdrawal history, and performing transfers.

## Account Types

When you create a Binance account, you automatically get a **Spot (`SPOT`)** account.

Depending on your trading needs, you may need to enable additional account types through the Binance website or interface:

*   **Margin (`MARGIN`) Account:** Required for margin trading. Refer to the [Margin Trading Guide](https://www.binance.com/en/support/faq/margin-trading-guide-360030300491) (Link needs verification).
*   **Futures (`FUTURES`) Account:** Required for trading USDⓈ-M and COIN-M Futures. Refer to the [Futures Trading Guide](https://www.binance.com/en/support/faq/futures-trading-guide-360033761971) (Link needs verification).
*   **Options (`OPTION`) Account:** Required for trading options. Refer to the [Option Trading Guide](https://www.binance.com/en/support/faq/options-trading-guide-360036950831) (Link needs verification).

## API Key Setup

Most API interactions, especially those involving private account data or trading, require an **API Key**.

1.  **Creation:** Generate API Keys through your Binance account security settings. ([How to Create an API Key](https://www.binance.com/en/support/faq/how-to-create-api-keys-on-binance-360002502072) - Link needs verification).
2.  **Security:**
    *   **NEVER share your API Key or Secret Key.** Treat them like passwords.
    *   If keys are compromised, delete them immediately and create new ones.
    *   It is highly recommended to configure **IP address restrictions** for your API keys for enhanced security.
3.  **Permissions:**
    *   By default, new API keys have `Enable Reading` permission only.
    *   To trade via the API, you need to enable trading permissions for the specific market (Spot, Futures, etc.) in the API key settings.
    *   To enable withdrawals via the API, you must explicitly check `Enable Withdrawals` in the API key settings (requires additional security verification like 2FA).

## General Conventions

*   Most endpoints return data in **JSON** format (either an object or an array).
*   Data is typically returned in **ascending** order (oldest first, newest last).
*   All time and timestamp-related fields are in **milliseconds (ms)** since the UNIX epoch.

See the [Endpoints Overview](./endpoints.md) and [Authentication](./authentication.md) pages for more details on specific URLs and securing your requests. 