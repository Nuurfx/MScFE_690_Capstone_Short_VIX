# MSCFE 690 Capstone Project: Volatility & Risk

**Authors:** Edgar Nava & Celestin NYANDWI 
**Institution:** WorldQuant University — Master of Science in Financial Engineering (MScFE)  
**Project Status:** Active / Capstone Phase  

---

## 🚀 Project Overview
This repository contains the Python code and data for our Capstone, **Short-VIX Exposure: An ETF-Based Trading System**. We study short-volatility exposure through ETFs and whether trading signals based on the Chicago Board Options Exchange (CBOE) Volatility Index ($\text{VIX}$), Volatility of Volatility Index ($\text{VVIX}$), and VIX Futures ETF ($\text{SVXY}$) can improve its results.

We begin by studying VIX statistics and volatility episodes to determine the VIX state boundaries. Then, we estimate separate transition matrices for 5-, 10-, and 15-trading-day horizons. Our intention is to identify possible “windows of opportunity” and test whether they help improve the performance of the trading signals.

We divide the data into development, validation, and test sets. We develop the trading signals using development data and refine them using validation data. We use the combined development and validation data to determine the final states and transition matrices. These remain fixed during testing. On the unseen test data, we compare the results of the signals with and without the opportunity windows.

The analysis includes SVXY data and a synthetic SVXY −1× series. We compare the trading strategy with continuous exposure to the same synthetic series and the S&P 500 total-return benchmark. We include trading costs and evaluate net returns, Sharpe ratios, maximum drawdowns, and other risk measures.

The data end date is September 16, 2026, and will remain fixed for the entire Capstone.

---

## 📁 Repository Structure

```text
mscfe_690_capstone/
├── data/
│   ├── raw/                           # Original source datasets
│   │   ├── VIX_data.csv                # VIX daily OHLC
│   │   ├── VVIX_data.csv               # VVIX daily OHLC
│   │   ├── SVXY_data.csv               # Observed SVXY daily OHLC
│   │   ├── SP500_data.csv              # S&P 500 price-index data
│   │   └── VIX_futures_data.csv        # VIX futures term structure, including F1 and F2
│   ├── processed/
│   │   ├── market_data.csv             # Cleaned and aligned market data
│   │   └── SVXY_synthetic_minus1x.csv  # Constructed synthetic −1× series
│   └── splits/
│       ├── development.csv            # Strategy development observations
│       ├── validation.csv             # Strategy refinement and selection observations
│       └── test.csv                   # Unseen observations for final evaluation
│
├── notebooks/
│   ├── 00_data_preparation.ipynb       # Data checks, alignment, synthetic series and splits
│   ├── 01_VIX_analysis.ipynb           # VIX statistics, volatility episodes and state boundaries
│   ├── 02_markov_analysis.ipynb        # Transition matrices, diagnostics and opportunity windows
│   ├── 03_strategy_development.ipynb   # Candidate trading rules and development simulations
│   ├── 04_strategy_validation.ipynb    # Refine/select rules and finalize the frozen model
│   └── 05_final_test.ipynb             # Unseen-data evaluation, comparisons and reporting
│
├── src/
│   ├── data_preparation.py             # Load, check, clean, align and split datasets
│   ├── vix_analysis.py                 # VIX statistics and volatility-episode analysis
│   ├── markov_model.py                 # State assignment and separate 5-, 10- and 15-day matrices
│   ├── markov_validation.py            # Transition diagnostics and Chapman–Kolmogorov checks
│   ├── opportunity_windows.py          # Translate transition information into window rules
│   ├── synthetic_svxy.py               # Construct the synthetic SVXY −1× series
│   ├── signals.py                      # Indicators, combined filters and trading signals
│   ├── backtest.py                     # Trades, execution timing, costs, cash and positions
│   ├── performance.py                  # Net returns, Sharpe ratio, drawdowns and risk statistics
│   └── reporting.py                    # Export settings, trade logs, tables and figures
│
├── config/
│   ├── data_settings.yaml             # Data paths, fixed cutoff and chronological split dates
│   └── strategy_settings.yaml         # Candidate rules, parameters, costs and execution settings
│
├── output/
│   ├── vix_analysis/                  # Descriptive statistics and volatility-episode figures
│   ├── frozen_model/                  # Final model estimated before testing
│   │   ├── state_boundaries.csv
│   │   ├── transition_matrix_5d.csv
│   │   ├── transition_matrix_10d.csv
│   │   ├── transition_matrix_15d.csv
│   │   ├── opportunity_windows.csv
│   │   └── final_settings.csv        # Selected rules and parameters used in the final test
│   ├── development/                   # Candidate results, trade logs and figures
│   ├── validation/                    # Validation results and strategy-selection comparisons
│   └── test/
│       ├── without_windows/           # Selected strategy without opportunity-window information
│       ├── with_windows/              # Same strategy incorporating opportunity-window information
│       ├── benchmarks/                # Continuous synthetic −1× exposure and S&P 500 total return
│       └── comparisons/               # Comparative performance tables and figures
│
├── requirements.txt                   # Python dependencies and versions
└── README.md                          # Project overview, methodology and execution instructions
