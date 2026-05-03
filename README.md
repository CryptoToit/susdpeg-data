# susdpeg-data

Public snapshot data mirror for the [**sUSD Peg Cockpit**](https://susdpeg.loopworks.io) dashboard.

This repository contains nothing but JSON snapshots. They are updated automatically every ~14 minutes by a Python collector pipeline (running in the source repo's GitHub Actions). Each file's `as_of` field is the moment the data was captured at source.

The dashboard's React client fetches these files at runtime via [jsdelivr](https://www.jsdelivr.com/), which CDN-mirrors GitHub repositories globally. Cache lag is ~5–10 minutes after each commit.

## Files

| Path | Panel it feeds |
|---|---|
| `data/peg/latest.json` | Peg Tracker · Trading Venues |
| `data/supply/latest.json` | Issued Supply |
| `data/scorecard/latest.json` | Recovery Program Scorecard |
| `data/yield/latest.json` | Stakeholder Yield Compare |
| `data/recovery_score/latest.json` | Recovery Score |
| `data/flow/latest.json` | Capital Flow Map |
| `data/trade_flow/latest.json` | Trade Flow |
| `data/radar/latest.json` | Sell-Pressure Radar |

## Sources

DefiLlama (price, supply, yield-pools), DexScreener (per-pool 24h volume + price), Curve API (Optimism stable-factory pools), public Ethereum + Optimism RPCs (on-chain `balanceOf`), Etherscan + Ethplorer (contract verification + holder labels), Synthetix open data.

## Source code

The source code that generates these snapshots is in a separate repository (currently private during the grant-pitch phase). Documentation of the pipeline architecture, data-source catalog, and supply reconciliation will be opened up once the project's grant outcomes are decided.

## Stability

These files are **for the dashboard's consumption**. We don't promise the schema will never change. If a panel's data shape evolves, the corresponding JSON shape evolves with it. Don't depend on these as a stable third-party API.

For the dashboard itself, see https://susdpeg.loopworks.io.
