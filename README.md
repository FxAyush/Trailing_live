TRAILING.live

AI-powered market crash early warning, geopolitical risk intelligence, and portfolio protection for U.S. and Indian markets.

TRAILING.live is a research-stage multi-agent financial intelligence system designed to answer:

How much market-crash risk is there over the next 15 trading sessions, why is that risk changing, and how should portfolio risk respond?

The system combines causal market stress indicators, geopolitical-risk data, a GBT + LSTM early-warning model, regime/risk agents, Monte Carlo and CVaR analysis, capital-preservation rules, and an explanation layer.

Important: TRAILING.live is an experimental research and decision-support system. It is not financial advice, does not guarantee returns, and does not guarantee that crashes will be predicted.

Latest Forward Forecast

Forecast origin / latest model inputs: 10 September 2026

These are frozen forward-test forecasts for the next 15 trading sessions. They are predictions made before the future outcome is known, so they should not be described as successful results until the full 15-session horizon has elapsed and the realized market path has been evaluated.

Market Next 15 trading-session crash probability Alert

U.S. --- S&P 500 proxy 5.3% Low India --- NIFTY 50 proxy 5.3% Low

For this model, a crash occurs if either of the following happens during the next 15 trading sessions:

forward close-to-close return is -5% or worse, or

maximum drawdown is -7% or worse.

Forward-test discipline

The forecast timestamp, model version, crash probability, and associated portfolio allocation should remain frozen after publication. Once 15 future trading sessions are available, the forecast can be resolved against the actual S&P 500 / NIFTY 50 path and added to the out-of-sample record.

2008 Historical Stress Test / Backtest

Using the existing real-return backtest, the strategy materially reduced losses during 2008 relative to a passive 70% equity / 30% bond benchmark.

The tested allocation rule uses yesterday's stress score, applies 5 bps one-way rebalance cost, and reduces equity exposure as risk rises:

70% → 50% → 25% equity

2008 result U.S. market India market

Model return -10.78% -14.48%

Passive 70/30 -23.48% -35.52% benchmark

Advantage +12.69 percentage +21.04 percentage points points

Loss reduction 54.1% 59.2%

Model max drawdown -26.49% -27.12%

Benchmark max -33.56% -45.78% drawdown

These figures are historical backtest results, not live returns and not guaranteed future performance. Backtest and forward-test evidence should remain clearly separated.

System Architecture

TRAILING.live is organized around six analytical layers and a five-agent decision system.

Layer 1 --- Macro Stress Index

Builds a causal 0--100 stress score from market and macro indicators such as volatility, yield-curve conditions, credit-spread proxies, market breadth, liquidity-style measures, and India-specific signals where reliable historical data is available.

The stress score measures the market environment; it is not the same as crash probability.

Layer 2 --- News & Geopolitical Risk

Monitors current geopolitical and market-moving news, including Iran/Israel/U.S. escalation, Strait of Hormuz and shipping risk, energy disruption, sanctions, nuclear risk, and major macro events.

Historical geopolitical ML features include AI-GPR measures and market transmission through Brent crude, gold, and the U.S. dollar.

Live headline risk is currently an explanatory/diagnostic overlay, not a direct ML feature, unless an equivalent historical series exists for training and validation.

Layer 3 --- Enhanced Market Data

Combines U.S. and Indian market information such as VIX / India VIX, S&P 500 / NIFTY, rates, credit proxies, USD/INR, Brent, gold, the U.S. dollar index, breadth, volatility, and other reproducible signals.

Production logic must never silently replace unavailable data with random values.

Layer 4 --- Alpha Research / Reasoning

Connects structured signals into an explainable macro thesis, for example:

geopolitical escalation → oil/shipping shock → inflation/import pressure → currency/flow pressure → higher market risk

Reasoning must remain traceable to real upstream evidence and clearly distinguish measured facts from inference.

Layer 5 --- Early Warning Model

The current early-warning architecture combines:

Gradient Boosted Trees (GBT)

LSTM sequence model

The fixed target is a crash during the next 15 sessions: return <= -5% or maximum drawdown <= -7%. Model development uses chronological/time-series validation rather than random train/test splitting.

Layer 6 --- Portfolio Risk & CVaR

Transforms risk estimates and regime information into portfolio recommendations using scenario analysis, Monte Carlo simulation, CVaR/tail-risk constraints, and defensive allocation logic.

The objective is risk-aware allocation --- not a promised rate of return.

Five-Agent Decision System

Regime Detection Agent --- classifies the environment into BULL, BEAR, SIDEWAYS, or CRISIS.

Risk Assessment Agent --- evaluates volatility, drawdown, turbulence, correlation behavior, and systemic stress.

FinRL Agent --- provides regime-aware RL allocation recommendations with out-of-distribution checks and defensive blending.

Capital Preservation Agent --- has rule-based veto authority when hard protection conditions are triggered.

Explanation Agent --- converts decisions into plain language with numerical statements traceable to upstream signals.

Data & Modeling Principles

Use real historical data whenever possible.

Document deterministic proxies.

Never inject known crisis dates into model features.

Never fabricate market returns or live financial signals.

Never use random values as production substitutes for unavailable data.

Do not backward-fill future observations into historical rows.

Rolling features must use only information available at that date.

Trading/allocation signals must be lagged where required.

Keep crash-target definitions fixed during fair model comparisons.

Use chronological, time-series, walk-forward, and frozen forward evaluation.

Never optimize solely to produce attractive AUC, Sharpe, or backtest returns.

Model Evaluation

Metric Meaning Better

ROC AUC Ability to rank crash Higher periods above non-crash periods

Average Precision (AP) Ability to identify Higher rare crash periods

Training AUC is diagnostic only. Primary evidence should come from time-series validation, walk-forward tests, and frozen forward forecasts.

Forward Testing vs Backtesting

Backtesting asks: How would this strategy have behaved on historical data under explicitly stated assumptions?

Forward testing asks: What did the model predict before the future happened, and what actually happened afterward?

For forward tests, TRAILING freezes the forecast date, model version, market, crash probability, alert level, and portfolio allocation when applicable. No prediction should be rewritten after observing the future.

Project Status

TRAILING.live should currently be considered a research/development project, not a validated production trading system.

Current work focuses on causal real-data pipelines, U.S. and India early-warning models, geopolitical-risk features, identical-fold model comparisons, LSTM overfitting control, probability calibration, walk-forward ensemble evaluation, frozen forward testing, and realistic portfolio tail-risk evaluation.

Core Repository Modules

app.py data_loader_v2.py signal_processor_v2.py early_warning_v2.py early_warning_v3.py geopolitical_risk.py backtester_v2.py forward_test_v2.py multi_agent_system.py regime_agent.py risk_agent.py safe_rl_agent.py ood_detector.py capital_preservation_agent.py portfolio_optimizer.py monte_carlo.py explanation_agent.py stress_tester.py

The exact active/obsolete dependency graph should be verified against the current repository before removing legacy files.

Responsible Performance Reporting

Do not publish experimental goals as validated results.

Claims such as a specific crash-detection rate, average warning lead time, or expected annual return should only be presented as validated performance after reproduction using real data, causal features, no leakage, fixed definitions, documented methodology, realistic costs, and frozen out-of-sample or walk-forward evaluation.

A lower but honest metric is more valuable than a higher metric produced by hindsight.

Disclaimer

TRAILING.live is an experimental financial research and decision-support project. Nothing in this repository constitutes investment advice, a recommendation to buy or sell securities, or a guarantee of future performance. Market forecasts can be wrong, historical relationships can change, and all investing involves risk, including loss of principal.

About

No description, website, or topics provided.
Resources
Readme
Activity
Stars
0 stars
Watchers
0 watching
Forks
