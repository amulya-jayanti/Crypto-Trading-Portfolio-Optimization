# Crypto-Trading-Portfolio-Optimization

Overview:\
Investors face increasing difficulty navigating the volatile and complex nature of the cryptocurrency market. This project builds a data-driven solution that leverages advanced forecasting and AI-based portfolio optimization to maximize returns and minimize risk in a multi-asset crypto portfolio.

Problem:\
Traditional financial models struggle to adapt to the rapid price swings, irregular patterns, and non-stationarity in crypto markets.

Gap:\
There's a lack of robust, domain-specific portfolio optimization frameworks tailored to crypto's dynamic behavior and diverse asset types.

Our Solution:\
We develop a pipeline that includes:

Predictive modeling of asset prices\
Technical indicators (RSI, SMA, volatility)\
Buy/sell logic to optimize portfolio allocation\
All driven by AI, time-series forecasting, and risk-adjusted decision-making.

Methodology:

Exploratory Data Analysis (EDA):

Evaluated 8 crypto assets over 4 years (2021–2025) on daily granularity\
Bitcoin dominates price movements; volume spikes reveal periods of market stress\
Strong correlation between BTC, ETH, SOL, BNB (> 0.75)\
Stablecoins like Tether show near-zero correlation

Data Preparation:

Feature engineering: lag features, returns, RSI, SMA-10, SMA-50\
Calculated 7-day rolling volatility and daily % returns\
Handled anomalies and ensured consistency across time

Predictive Modeling:

Model	Strengths	Limitations\
ARIMA/SARIMA	Captures trends/seasonality short-term	Struggles with high volatility\
Prophet	Flexible, good with changepoints	May lag on fast reversals\
LSTM	Learns long-term dependencies	Prone to overfitting without regularization\
Prediction Task: Forecast next-day closing price for each asset

Portfolio Optimization:

Objective: Maximize expected return; minimize risk\
Initial Wallet: Simulated balance for allocation\
Buy/Sell Logic\
Buy: Top assets based on predicted % return\
Stop-Loss: -10%, Take-Profit: +20%\
Risk Appetite: Tunable (0 = conservative, 1 = aggressive)\
Daily Simulation: Dynamic rebalancing based on model outputs

Key Features:

Feature	Description\
datetime	Timestamp of record\
open / high / low / close	Price range during interval\
volume_crypto	Asset volume traded\
volume_fiat	Fiat volume (e.g., USD) traded\
RSI	Momentum indicator (overbought > 70, oversold < 30)\
SMA	Simple moving averages (10-day, 50-day)

Hypotheses & Assumptions:

Historical price trends, volatility, and volume influence future returns\
Seasonality and cycles exist in crypto prices\
Technical indicators improve predictability

Recommendations:

Use top predicted return assets for allocation\
Monitor RSI to identify overbought/oversold zones\
Rebalance portfolio daily for maximum risk-adjusted gains

Future Scope:

🔧 Model Enhancements\
Incorporate exogenous signals: stock indices, interest rates, macroeconomic indicators\
Improve trend detection (e.g., Prophet changepoint tuning)\
Use attention-based models (e.g., Transformers)

🧮 Portfolio Enhancements\
Reinforcement Learning agents for real-time allocation\
Dynamic risk scoring based on volatility bands

⚙️ Deployment\
Dockerize and deploy model as an endpoint\
Add live data pipeline for continuous training & monitoring

📚 Learning Outcomes\
Time series forecasting with Prophet, LSTM, ARIMA\
Technical analysis using financial indicators\
Risk-aware portfolio allocation logic\
Bridging machine learning with investment decision-making

📌 Assets\
8 Cryptocurrencies: Bitcoin, Ethereum, Tether, Solana, Dogecoin, TrumpCoin, XRP, Binance Coin\
Time Period: Jan 2021 – Jan 2025\
Level: Daily frequency

Prophet Model Results:
Asset     Train sMAPE   Test sMAPE
Solana     2.27%          1.78%
Doge Coin  3.69%          2.07%
Ethereum   1.08%          0.63%
Bitcoin    0.83%          0.87%

