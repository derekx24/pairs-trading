# Pairs Trading Strategy

This project explores a pairs trading strategy based on cointegration using Python. The idea is to find two stocks that move together over time. When the price difference/spread between them gets unusually large or small, the strategy generates a signal to trade.This works because we expect the prices to eventually return to their typical pattern.

By monitoring how much the spread deviates from its average, we can take long or short positions in the pair, aiming to profit when the spread eventually reverts to the mean.

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
   - Calculated rolling mean and standard deviation of the spread
   - Generated signals:
     - **Enter short** if Z-score > 2
     - **Enter long** if Z-score < -2
     - **Exit** if Z-score crosses 0

5. **Backtesting**
   - Simulated daily returns using trading signals
   - Calculated and plotted cumulative return over time

---

## How to run

1. Clone the repo:
   ```bash
   git clone https://github.com/derekx24/pairs-trading.git
   cd pairs-trading
   ```

2. Install dependancies:
    ```bash
    pip install -r requirements.txt
    ```

3. Run the Jupyter notebook under the `notebooks` directory