# Nifty 50 Algorithmic Reversal Engine

## 🔭 Project Overview
This project is an automated **paper trading** framework developed for the National Stock Exchange (NSE). The core logic is built around a "Dip & Bounce" mean-reversion strategy, which I conceptualized after several months of observing price action structures in the Nifty 50 index.

Rather than relying on market intuition, I transitioned to a quantitative approach by conducting a manual backtest on a sample set of trading sessions. The data validated a consistent recurring trend where the index sweeps liquidity (the "Dip") before executing a sharp reversal (the "Bounce").

## 📈 Strategic Analysis & Paper Trading Performance
The "Dip & Bounce" strategy is built on a high-expectancy mathematical model. Currently operating in a **Live Paper Trading** environment, the system is designed to maintain profitability even with a win rate as low as **35%** by targeting a strict **1:2 Risk-to-Reward (RR)** ratio.

### Key Research Findings:

<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/cd436cab-4158-4c5c-a589-8c094efdfef8" />

Based on my preliminary backtest and paper trading data, the strategy captured significant intraday moves:
* **Peak Performance:** Captured a **100%+ move** in a single session.
* **Alpha Generation:** Consistent "Bounce" triggers were identified across both Bullish (CE) and Bearish (PE) environments, proving the strategy's adaptability to different market regimes.
* **Risk Management:** The system utilizes **Average True Range (ATR)** to set dynamic, volatility-adjusted stop losses, ensuring the engine "breathes" with the market.

> **Note:** Comprehensive paper trading logs and testing data are currently being processed. Verified equity curves and drawdown statistics will be updated here when ready.

## 🛠️ Technical Architecture
This repository demonstrates the **Paper Trading Infrastructure** and **Data Pipeline** required for systematic trading.

* **Multi-Source Ingestion:** Syncs overnight US Futures (Dow/S&P/Nasdaq) via `yfinance` to establish a global sentiment bias before the Indian market opens.
* **Domestic Sentiment Filter:** Analyzes India VIX and Put-Call Ratio (PCR) to refine entry probability.
* **Non-Regressive Trailing Stop (TSL):** A custom-built execution loop that "ratchets" the stop-loss upward as the trade moves in favor, allowing the engine to capture "home run" moves during trending days.
* **Automated Logging:** Every execution, skip reason, and net PnL metric is logged to `paper_trade_log.csv` for performance review and audit trails.


## 📂 Repository Structure
* `trading_engine.py`: The core execution engine (Logic triggers abstracted for IP protection).
* `.env.example`: Template for secure API credential management.
* `paper_trade_log.csv`: Persistent log for performance tracking and post-trade analysis.

## 🚀 Future Roadmap
* [ ] Transition from Paper Trading to Live Capital Deployment.
* [ ] Integration of Machine Learning (Random Forest) to filter "False Bounces."
* [ ] Multi-index support (BankNifty/FinNifty).

---

## 🔒 Confidentiality Note
> To protect the proprietary nature of the "Dip & Bounce" strategy, specific mathematical constants and entry thresholds have been moved to environment variables and are not included in the public source code. This repository serves as a showcase of **System Design**, **API Integration**, and **Data Analysis** capabilities.
