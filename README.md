# 🥒 David Indicators Confluence

Multi-timeframe signal dashboard for retail traders who prefer **few, high-conviction entries**.

## Strategy

6 main signals with freshness tracking, plus multi-timeframe alignment (1D / 1S / 4H):

| Signal | Description |
|---|---|
| S1: MACD ↑ | MACD line crosses above signal line |
| S2: PVI ↑ | Price-Volume Index crosses above EMA25 |
| S3: Media K | Koncorde media line enters the area |
| S4: AO verde | Awesome Oscillator changes from red to green |
| S5: Bitman ↑ | Bitman = IMPULSO ALCISTA |
| S6: Azul K ↑ | Koncorde azul crosses from negative to positive |

## Labels

| Label | Condition | Directional accuracy (~40 bars) |
|---|---|---|
| ⚡ BOOM ULTRA | EMBRYO 1D + 1S + 4H aligned | ~100% |
| 🔥 BOOM | EMBRYO 1D + 1S + SPY > EMA200 | ~76% |
| 🟢 NO ESTÁ MUY MAL | EMBRYO in 1D | ~66% |
| ⚠️ SALIDA | MATURATION or DECLINE | — |

## Sync Bar

The sync bar shows at a glance which timeframes are aligned:

```
⏱ EMBRION  1D ●  1S ●  4H ○  SPY ●
```

- **●** (green dot) = timeframe is aligned (EMBRYO / EARLY SIGNALS)
- **○** (dim dot) = not aligned

## Charts (Tab 2)

9 panels: Candles · Volume · RSI · ADX+AO · Koncorde · BBWP · PVI · MACD · **Stochastic (18,5,9)**

The Stochastic shows ▲ at bullish crosses in the 20-40 zone.

## Context

- **SPY > EMA200**: green/red banner at the top indicates whether the general market supports long entries.
- **Ticker names**: company names shown alongside ticker symbols for clarity.

## Run locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

## Project structure

| File | Purpose |
|---|---|
| `app.py` | Streamlit dashboard (Tab 1: signals, Tab 2: charts) |
| `indicators.py` | Core signal engine (6 signals, phases, labels) |
| `config.py` | Shared config: tickers, names, groups (no circular imports) |
| `scripts/daily_snapshot.py` | Daily snapshot generator for GitHub Actions |
| `requirements.txt` | Python dependencies |
| `.github/workflows/scheduled_run.yml` | Scheduled daily automation |

## Deploy on Streamlit Cloud

1. Push this repo to GitHub
2. Go to [share.streamlit.io](https://share.streamlit.io)
3. Connect the repo → Deploy

## Backtesting Results

Tested on 17 tickers, 2 years, daily timeframe:

| Signal | Win rate 40 bars | Avg return 40 bars |
|---|---|---|
| EMBRYO 1D | 66.5% | +4.9% |
| EMBRYO 1D + 1S | 76.5% | — |
| EMBRYO 1D + 1S + 4H | 100% | — |
| Random entry | 56.3% | +3.6% |

## License

MIT
