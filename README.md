# MSCFE 690 Capstone Project: Volatility & Risk

**Authors:** Edgar Nava & Celestin NYANDWI 
**Institution:** WorldQuant University — Master of Science in Financial Engineering (MScFE)  
**Project Status:** Active / Capstone Phase  

---

## 🚀 Project Overview

This repository houses the quantitative engine and analytical framework for our MScFE Capstone Project. The project investigates **market volatility Index regime-switching dynamics** using daily time-series data for the Chicago Board Options Exchange (CBOE) Volatility Index ($\text{VIX}$), Volatility of Volatility Index ($\text{VVIX}$), and Short VIX Futures ETF ($\text{SVXY}$).

and risk paramaters By modeling market sentiment through discrete economic regimes, this engine computes empirical state distributions, expected regime residence times, multi-horizon transition probability matrices ($P^{(k)}$), and Chapman-Kolmogorov validation tests to assess path memory and volatility clustering.

---

## 📁 Repository Structure

```text
mscfe_690_capstone/
├── data/
│   ├── VIX_data.csv          # CBOE Volatility Index daily OHLC (2004–2026)
│   ├── VVIX_data.csv         # CBOE Volatility of Volatility Index daily data
│   └── SVXY_data.csv         # ProShares Short VIX Short-Term Futures ETF data
├── notebooks/
│   └── 01_markov_analysis.ipynb # Interactive Jupyter notebook for exploratory analysis
├── src/
│   ├── markov_model.py       # Core Markov state discretization & transition engine
│   └── markov_validation.py  # Chapman-Kolmogorov tests & joint VIX-VVIX mapping
├── output/                   # Generated transition matrices, CSV summaries & figures
└── README.md                 # Project documentation
