Overview

This project implements a complete systematic trading workflow:
	1.	Machine Learning Model (Forecasting Layer)
	•	AR-based model predicting short-term returns
	•	Supervised learning using PyTorch
	•	Evaluation on out-of-sample data
	•	Exportable trained model weights
	2.	Strategy Logic (Research Layer)
	•	Rules-based long/short signals
	•	Uses ML forecasts as directional input
	•	Position sizing and compounding returns
	•	Backtesting with Polars / Python
	•	12h timeframe signals
	3.	Execution Engine (Trading Layer)
	•	Exchange interface for Binance USDT-M Futures
	•	Order routing for market orders
	•	Reduce-only closing logic
	•	Leverage/precision handling
	•	Clean interface for going live or using testnet

   1. Machine Learning Model

The forecasting model is implemented in:
notebooks/ADA_ML_model.ipynb

Key features:
	•	AR(2)-style structure using lagged returns
	•	MSE loss function
	•	Clean PyTorch implementation
	•	Model trained on historical OHLCV data
	•	Saved weights included in model_weights.pth

Outputs:
	•	12h price-return prediction
	•	Signal direction
	•	Signal confidence


  2. Strategy Implementation

Strategy research is in:
notebooks/ADA_StrategyImplementation.ipynb

Main components:
	•	Transforms ML forecasts into trading signals
	•	Long/short entry rules
	•	Exit rules based on signal reversal
	•	Compounding position sizing
	•	Transaction-level PnL
	•	Cumulative returns
	•	Equity curve tracking

The strategy strictly follows the logic:
	•	Close positions at the end of candle t
	•	Open new positions at the start of candle t+1 using previous signal

  3. Automated Order Execution

Execution logic is contained in:
notebooks/ADA_executing_orders.ipynb

Tech Stack
	•	Python
	•	Polars for high-performance data handling
	•	PyTorch for machine learning
	•	Matplotlib / Altair for visualization
	•	Requests / Web APIs
	•	Binance Futures API
	•	Jupyter Notebooks for research environment


 How to Run the Project
 1) Create a research environment
    conda create --name research python=3.12
    conda activate research
 2) Install dependencies
    conda install -c conda-forge -c pytorch polars pytorch requests scipy matplotlib altair tqdm vegafusion
 3) Open the notebooks
    jupyter notebook
    
Then open:
	•	ADA_ML_model.ipynb
	•	ADA_StrategyImplementation.ipynb
	•	ADA_executing_orders.ipynb

  For questions, collaboration, or opportunities:
LinkedIn: https://www.linkedin.com/in/luca-toselli-ab85292a8/
