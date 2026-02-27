# portfolio-monte-carlo
Monte Carlo portfolio simulator
# Portfolio Monte Carlo Simulator

A Python tool simulating 5-year performance of a diversified global 
portfolio across 18 assets using Monte Carlo methods.

## What it does
- Downloads live price data via yfinance
- Runs 10,000 simulations using log-normal return modelling
- Computes VaR, CVaR, Sharpe Ratio and Sortino Ratio
- Outputs a distribution histogram with annotated risk metrics

## Technologies
Python · NumPy · Matplotlib · yfinance

## How to Run
pip install numpy matplotlib yfinance
python monte_carlo.py
