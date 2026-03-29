# Real-Time Crypto Trading Signal Pipeline

A real-time cryptocurrency trading system that ingests exchange trade data, converts it into 1-minute candles, generates buy/sell signals using a machine learning model, retrains the model hourly, and tracks portfolio performance through a Streamlit dashboard.

## Overview

This project was built to support short-horizon crypto trading by focusing on **signal generation** rather than exact price prediction. The system continuously ingests market data, creates candle-level features, runs inference on new candles, retrains the model on a schedule, and executes strategy decisions through a trade bot.

### Core workflow
- **Realtime market ingestion** from Kraken trade data
- **1-minute candle generation** from raw trades
- **ML-based buy/sell signal prediction**
- **Trade execution every 5 minutes**
- **Model retraining every hour**
- **Live dashboard for candles, model metrics, and strategy balances**

## Architecture

The application is organized as a **containerized multi-service pipeline** using Docker and Docker Compose.

### Services
- **base**: shared runtime image and dependencies
- **backfill**: fetches historical trades and converts them into candles
- **realtime**: streams new trades continuously
- **candle_maker**: builds realtime candles from incoming trade data
- **predict**: processes new candles and generates predictions
- **trade_bot**: executes strategy decisions on a scheduled interval
- **train**: retrains the ML model on a scheduled interval
- **streamlit_app**: serves the monitoring dashboard

## Tech Stack

- **Python**
- **Docker**
- **Docker Compose**
- **Streamlit**
- **tmux**
- **cron**
- **Kraken market data**
- **Technical analysis / time-series feature engineering**
- **Optuna-based feature tuning**

## Repository Structure

```text
.
├── data/
│   ├── historical/
│   └── models/
├── services/
│   ├── backfill/
│   ├── base/
│   ├── candle_maker/
│   ├── dev_box/
│   ├── predict/
│   ├── realtime/
│   ├── streamlit_app/
│   ├── trade_bot/
│   └── train/
├── docker-compose.yml
├── readme.md
└── commands.md

