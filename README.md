# News Driven S&P 500 Return and Volatility Forecasting

A time-series forecasting project investigating whether financial news sentiment and risk signals extracted from news (in this case GDELT Data) can improve forecasts of **S&P 500 returns and volatility**.

The project combines financial time-series models with news-derived features and is designed to eventually support a daily prediction pipeline.

---

## Overview

Financial markets are influenced not only by historical price movements but also by information arriving through news.

This project investigates whether information extracted from historical news can provide additional predictive power for:

1. **Next-day S&P 500 returns**
2. **Next-day S&P 500 volatility**

The project combines:

- S&P 500 historical price data
- GDELT financial/news data
- News tone/sentiment
- Daily news volume
- A news-based risk signal
- ARIMA / ARIMAX models for returns
- GARCH / GARCH-X models for volatility

The ultimate goal is to develop a pipeline that can process new news and market data on a daily basis and generate updated forecasts.

---

# Project Architecture

```text
                  GDELT News
                      |
                      v
              Extract V2Tone
                      |
                      v
            Daily News Aggregation
                      |
             +--------+--------+
             |                 |
             v                 v
        Average Tone       News Count
             |                 |
             +--------+--------+
                      |
                      v
                Risk Signal
                      |
                      v
              +-------+-------+
              |               |
              v               v
          ARIMAX           GARCH-X
              |               |
              v               v
       Return Forecast   Volatility Forecast
