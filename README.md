# ChatGPT Trading Signal Bridge (Starter)

This repository now includes a **starter bot** that connects the OpenAI API (ChatGPT) to Alpaca for generating and executing trading signals.

> ⚠️ High risk: live trading can lose money quickly. Start in paper mode and test thoroughly.

## What it does

- Pulls recent 1-minute bars for a symbol from Alpaca market data.
- Sends compact market context to ChatGPT.
- Expects strict JSON response: `BUY`, `SELL`, or `HOLD`.
- Applies guardrails (confidence threshold, max position size).
- Places market orders through Alpaca trading API.

## Quick start

1. Create and activate a Python virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Copy env template and fill values:

```bash
cp .env.example .env
```

4. Run in paper mode:

```bash
python trading_signal_bot.py
```

## Environment variables

- `OPENAI_API_KEY`: OpenAI key.
- `OPENAI_MODEL`: Model name (default `gpt-4o-mini`).
- `ALPACA_API_KEY`: Alpaca API key.
- `ALPACA_API_SECRET`: Alpaca API secret.
- `ALPACA_BASE_URL`: Alpaca trading URL (`https://paper-api.alpaca.markets` for paper).
- `ALPACA_DATA_URL`: Alpaca data URL (`https://data.alpaca.markets`).
- `SYMBOL`: Trading symbol (default `AAPL`).
- `BAR_TIMEFRAME_MINUTES`: Bar timeframe in minutes (default `1`).
- `BAR_LOOKBACK`: Number of bars to send to model (default `30`).
- `CONFIDENCE_THRESHOLD`: Minimum confidence from model to act (default `0.65`).
- `MAX_ORDER_QTY`: Maximum quantity per order (default `1`).
- `POLL_SECONDS`: Loop delay in seconds (default `60`).

## Notes

- This is intentionally minimal and educational.
- Add stronger risk management (daily loss limits, circuit breakers, max drawdown).
- Validate strategy with backtests + paper trading before live deployment.
