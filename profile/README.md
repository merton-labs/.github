# Merton Labs

**Merton** is an open-source, self-hosted investment portfolio tracker. You
run it on your own machine or server, and your data stays in your own
SQLite database. Several people can use one install, and each person's
portfolios stay private.

> **Status:** 0.1.0, the first release (the MVP). See the release notes for
> [merton-api](https://github.com/merton-labs/merton-api/releases/tag/v0.1.0)
> and [merton-web](https://github.com/merton-labs/merton-web/releases/tag/v0.1.0).

## What it does

- **Portfolios:** as many as you like, each with a base currency, and
  archive and restore.
- **Assets:** Thai and international stocks, ETFs, mutual funds, cash and
  bank deposits, with several cash accounts in different currencies.
- **Transactions:**
  - buys and sells, with FIFO lots
  - dividends, interest, fees, taxes, tax returns and other expenses
  - deposits, withdrawals, cash transfers and FX exchanges
  - stock dividends, stock splits and reverse splits
  - opening positions and balances for holdings you already own
- **Reporting:** holdings, valuation and allocation by asset class at any
  date, from prices and FX rates that you enter.
- **Exact money:** amounts are exact decimals end to end, never floats.

The transaction forms follow
[Snowball Analytics](https://snowball-analytics.com).

## Repositories

| Repository                                              | What it is                                        | Stack                                   |
| ------------------------------------------------------- | ------------------------------------------------- | --------------------------------------- |
| [merton-api](https://github.com/merton-labs/merton-api) | REST backend: accounts, ledger, FIFO, valuation   | Rust, Axum, SeaORM, SQLite              |
| [merton-web](https://github.com/merton-labs/merton-web) | Web app, plus the full-stack Docker Compose setup | SvelteKit (Svelte 5), Tailwind CSS, Bun |

## Quick start

You need Docker with Compose, or Podman with a Compose provider. Clone both
repositories side by side, then start the stack from `merton-web`:

```sh
git clone https://github.com/merton-labs/merton-api.git
git clone https://github.com/merton-labs/merton-web.git
cd merton-web
cp .env.example .env
# Set APP_SECRET_KEY in .env, e.g. to the output of: openssl rand -base64 48
docker compose up --build
```

Then open <http://localhost:8080> and create an account.
[merton-web's README](https://github.com/merton-labs/merton-web#running-with-docker-compose)
covers configuration and the smoke test.

## Not included

- CSV import and export are planned for after the MVP.
- Market data is not fetched automatically. You enter prices and FX
  rates yourself.
- There are no brokerage integrations, crypto, bonds, derivatives or
  margin, and no sharing between users.

## License

[Apache License 2.0](https://github.com/merton-labs/merton-api/blob/main/LICENSE).
