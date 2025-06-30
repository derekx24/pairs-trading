# Pairs Trading Strategy

This project implements a cointegration-based pairs trading strategy using Python. The goal is to identify pairs of assets that exhibit a stable long-term relationship and generate trading signals when their spread diverges significantly from its mean.

---

## Steps

1. **Data Collection**
   - Downloaded historical price data using `yfinance`
   - Extracted and clean the closing prices
   - Plotted the closing price over a four year period (2020-2024)

2. **Cointegration Test**
   - Performed Engle-Granger two-step method to test long-run relationship
   - BRK-B and MSFT showed moderate cointegration

3. **Spread Calculation**
   - Estimated hedge ratio (β) using linear regression
   - Computed spread as: `spread = price_BRK - β × price_MSFT`

4. **Z-score Signal Generation**
   - Calculated rolling mean and std dev of the spread
   - Generated signals:
     - **Enter short** if Z-score > +2
     - **Enter long** if Z-score < -2
     - **Exit** if Z-score crosses 0

5. **Backtesting**
   - Simulated daily returns using lagged trading signals
   - Calculated and plotted cumulative return over time

---

## How to run

1. Clone the repo:
   ```bash
   git clone https://github.com/yourname/pairs-trading.git
   cd pairs-trading
   ```

2. Install dependancies:
    ```bash
    pip install -r requirements.txt
    ```

3. Run the Jupyter notebook under the `notebooks` directory