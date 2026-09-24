# Python-STOCK-PRICE-MONTE-CARLO-SIMULATOR


1. Project Overview
   
The Stock Price Monte Carlo Simulator is a Python-based financial analytics project that uses NumPy to simulate stock-price movements and portfolio outcomes under a set of assumed market conditions. The project was developed progressively, beginning with a basic stock-price simulation and expanding into portfolio analysis, risk measurement, Monte Carlo simulation, visualization, and percentile-based scenario analysis.
The primary objective is to understand how numerical computing, statistical simulation, and financial risk concepts can be implemented using Python and NumPy without relying on specialized finance libraries.
Important: The simulated results are mathematical scenarios based on user-defined assumptions. They are not forecasts, investment recommendations, or predictions of actual market performance.

2. Project Objectives

1. Simulate daily stock-price movements using randomly generated returns.
2. Calculate portfolio value, profit/loss, and investment return.
3. Measure basic investment risk using financial risk metrics.
4. Generate 1,000 possible stock-price paths using Monte Carlo simulation.
5. Estimate the simulated proportion of profitable and loss outcomes.
6. Visualize simulated stock-price paths and the distribution of final portfolio values.
7. Analyze simulated outcomes using percentiles and scenario analysis.
8. Practice NumPy arrays, vectorization, statistics, random simulation, and Matplotlib visualization.

3. Technologies Used

•	Python
•	NumPy — numerical calculations, random simulation, arrays, statistics, and vectorized operations.
•	Matplotlib — visualization of simulated price paths and portfolio-value distributions.
•	Google Colab / Jupyter Notebook — development and execution environment.
The core simulation does not require pandas, scikit-learn, yfinance, or a specialized financial-data API.

4. Project Development 

Step 1 — Stock Price Simulation
The first version creates one possible stock-price path over 252 trading days. Daily returns are generated using a normal distribution and converted into stock prices using cumulative products.
Main parameters:
•	Initial stock price: $100
•	Trading days: 252
•	Expected daily return: 0.05%
•	Daily volatility: 2%
•	Random seed: 42
Important NumPy operations:
•	np.random.normal()
•	np.cumprod()
•	np.insert()
•	np.mean()
•	np.std()
•	np.max()
•	np.min()
The version calculates the final stock price, maximum and minimum price, total return, average daily return, and daily volatility.

Step 2 — Portfolio Simulation
Version 2 extends the stock-price simulation into an investment scenario. An initial investment of $10,000 is made when the simulated stock price is $100.
Number of shares:
shares = initial_investment / initial_price
This results in 100 shares. The model then calculates the final portfolio value, profit or loss, and portfolio return based on the simulated final stock price.

Step 3 — Risk Analysis
Version 3 introduces financial risk metrics to evaluate the simulated price path.

Maximum Drawdown
Maximum drawdown measures the largest decline from a previous running peak.
running_max = np.maximum.accumulate(prices)
drawdown = (prices - running_max) / running_max

Sharpe Ratio
A simplified annualized Sharpe ratio is calculated using the simulated mean return and volatility, with a 0% risk-free-rate assumption.
sharpe_ratio = (np.mean(random_returns) / np.std(random_returns)) * np.sqrt(252)

95% Value at Risk
A simplified historical-style VaR is estimated using the 5th percentile of simulated daily returns.
var_95 = np.percentile(random_returns, 5)
Additional risk metrics include the best trading day and worst trading day.

Step 4 — Monte Carlo Simulation
Instead of generating one possible future, Version 4 generates 1,000 possible stock-price paths, with each path containing 252 trading days.
The return matrix therefore has the shape:
(1000, 252)
Rows represent simulations and columns represent trading days. NumPy vectorization is used to perform the calculations efficiently.
random_returns = np.random.normal(
    daily_return,
    daily_volatility,
    (num_simulations, days)
)

price_paths = initial_price * np.cumprod(
    1 + random_returns,
    axis=1
)

Final portfolio results from the completed simulation:
Metric	Result
Number of simulations	1,000
Trading days	252
Initial investment	$10,000
Average final value	$11,326.91
Median final value	$10,921.05
Best final value	$25,967.81
Worst final value	$3,887.48
Profitable simulations	610
Loss simulations	390
Simulated probability of profit	61%
Simulated probability of loss	39%
These results describe the simulated distribution produced by the selected assumptions. They should not be interpreted as predictions of actual market outcomes.

5. Visualization 📊📈

Matplotlib is introduced for visual analysis. Two main visualizations were created.

5.1 Monte Carlo Stock Price Paths
The first chart displays 100 of the 1,000 simulated stock-price paths. All paths begin near the initial price and gradually spread as random daily returns accumulate.

<img width="712" height="393" alt="Screenshot 2026-09-23 202218" src="https://github.com/user-attachments/assets/2a86ff88-be42-4161-8880-1881b288c2bc" />

 
5.2 Distribution of Final Portfolio Values
The second chart is a histogram of the 1,000 final portfolio values. It includes reference lines for the initial investment, mean, and median, making it easier to compare the simulated outcomes with the starting $10,000 investment.

<img width="713" height="461" alt="Screenshot 2026-09-23 202844" src="https://github.com/user-attachments/assets/944ffb4c-2353-4387-aacf-13a5629bb3e5" />

6. Percentile & Scenario Analysis 💯

The final stage analyzes the distribution of final portfolio values using percentiles. Percentiles help describe different parts of the simulated outcome distribution.

Percentile	Portfolio Value	Simulated Return
5th	$6,395.82	-36.04%
25th	$8,657.42	-13.43%
50th	$10,921.05	+9.21%
75th	$13,312.98	+33.13%
95th	$18,080.52	+80.81%

Scenario interpretation used in the project:
•	5th percentile — downside scenario
•	25th percentile — lower scenario
•	50th percentile — median scenario
•	75th percentile — upper scenario
•	95th percentile — upside scenario
These scenarios describe the simulated distribution under the model assumptions and are not forecasts.

7. Key NumPy Concepts Practiced 🔢

•	Random number generation with np.random.normal()
•	Cumulative products with np.cumprod()
•	Array insertion with np.insert()
•	Mean and median with np.mean() and np.median()
•	Standard deviation with np.std()
•	Maximum and minimum values with np.max() and np.min()
•	Running maximum with np.maximum.accumulate()
•	Percentile analysis with np.percentile()
•	Counting conditions with np.sum()
•	Annualization with np.sqrt()
•	1D and 2D NumPy arrays
•	Array indexing and slicing
•	Vectorized calculations
•	The axis parameter, especially axis=1

8. Key Financial Concepts Practiced 💱

•	Daily returns
•	Stock-price simulation
•	Portfolio value
•	Profit and loss
•	Portfolio return
•	Volatility
•	Maximum drawdown
•	Sharpe ratio
•	Value at Risk (VaR)
•	Monte Carlo simulation
•	Simulated probability of profit/loss
•	Percentile analysis
•	Scenario analysis

9. Project Structure ⚙️

Stock-Price-Monte-Carlo-Simulator/
│
├── stock_simulator.py
├── README.md
├── requirements.txt
└── screenshots/
    ├── monte_carlo_price_paths.png
    └── portfolio_value_distribution.png

10. How to Run 👩‍💻

Install the required packages:
pip install numpy matplotlib
Then run the Python script:
python stock_simulator.py
The program prints the simulation statistics and generates the visualization charts.

11. Main Assumptions 💵

•	Initial stock price = $100
•	Initial investment = $10,000
•	Trading days = 252
•	Number of Monte Carlo simulations = 1,000
•	Expected daily return = 0.05%
•	Daily volatility = 2%
•	Random seed = 42
•	Risk-free rate = 0% for the simplified Sharpe-ratio calculation

12. Learning Outcome 🔳

This project demonstrates how Python and NumPy can be used to build a financial simulation from the ground up. It combines Python programming, numerical computing, statistics, finance, Monte Carlo simulation, risk analysis, and data visualization.
The project is particularly relevant for demonstrating practical skills in Finance, Business Analytics, Quantitative Analysis, and Python-based Data Analytics.

13. About 🙋‍♀️
Shrestha Sarkar
PGDM — Finance Major | Business Analytics Minor
Skills demonstrated: Python, NumPy, Matplotlib, Financial Analysis, Risk Analysis, Statistical Simulation, Monte Carlo Simulation, and Data Visualization.

14. License 📄

This project is licensed under the [MIT License](LICENSE).
