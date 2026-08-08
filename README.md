# Project Sentinel V2

Institutional-style Forex Signal Intelligence Platform.
Deterministic. Rule-based. Explainable.

## Status
Milestone: M0 — Project Foundation (in progress)

## What this is
Not a trading bot. Not an auto-execution system by default.
A signal intelligence platform that monitors multiple Forex pairs
across three timeframes and publishes explainable trade signals
only when objective evidence supports one.

## Core principles
- No evidence, no signal.
- Every decision must be deterministic and reproducible.
- Every module has exactly one responsibility.
- Configuration over hardcoding.
- Backtest before build — no live signals until historical
  validation passes.

## Architecture (canonical pipeline)
Market Data
  -> [per timeframe: Swing Detection -> Market Structure]
  -> MTF Bias
  -> Trendline
  -> Breakout
  -> Retest
  -> Manipulation Intelligence
  -> Confirmation
  -> Signal Qualification
  -> Trade Planning
  -> Signal Publishing
  -> Trade Lifecycle
  -> Performance Intelligence
  -> AI Confidence (downstream advisor only, never decision-maker)

## Repo structure
- `src/`    — engine code
- `config/` — configuration and thresholds (no secrets, ever)
- `tests/`  — tests, one set per engine

## Development discipline
- Backtest-first: M7 and M13 are go/no-go research checkpoints.
- Research-notebook process for every strategy change:
  hypothesis -> test -> result -> interpretation -> decision.
- No look-ahead bias in any historical test.
- Conservative assumption used for any ambiguous backtest outcome.

## Relationship to V1
This is a separate, from-scratch rebuild. The V1 Telegram signal
bot remains untouched and operates independently.
