# Python-STOCK-PRICE-MONTE-CARLO-SIMULATOR


A. Project Overview
   
The Stock Price Monte Carlo Simulator is a Python-based financial analytics project that uses NumPy to simulate stock-price movements and portfolio outcomes under a set of assumed market conditions. The project was developed progressively, beginning with a basic stock-price simulation and expanding into portfolio analysis, risk measurement, Monte Carlo simulation, visualization, and percentile-based scenario analysis.
The primary objective is to understand how numerical computing, statistical simulation, and financial risk concepts can be implemented using Python and NumPy without relying on specialized finance libraries.
Important: The simulated results are mathematical scenarios based on user-defined assumptions. They are not forecasts, investment recommendations, or predictions of actual market performance.

B. Project Objectives

1. Simulate daily stock-price movements using randomly generated returns.
2. Calculate portfolio value, profit/loss, and investment return.
3. Measure basic investment risk using financial risk metrics.
4. Generate 1,000 possible stock-price paths using Monte Carlo simulation.
5. Estimate the simulated proportion of profitable and loss outcomes.
6. Visualize simulated stock-price paths and the distribution of final portfolio values.
7. Analyze simulated outcomes using percentiles and scenario analysis.
8. Practice NumPy arrays, vectorization, statistics, random simulation, and Matplotlib visualization.

C. Technologies Used

1. Python
2. NumPy — numerical calculations, random simulation, arrays, statistics, and vectorized operations.
3. Matplotlib — visualization of simulated price paths and portfolio-value distributions.
4. Google Colab / Jupyter Notebook — development and execution environment.
The core simulation does not require pandas, scikit-learn, yfinance, or a specialized financial-data API.

D. Project Development 

_Step 1 — Stock Price Simulation_
The first version creates one possible stock-price path over 252 trading days. Daily returns are generated using a normal distribution and converted into stock prices using cumulative products.

_Main parameters:_

<img width="488" height="210" alt="Screenshot 2026-09-23 195746" src="https://github.com/user-attachments/assets/2616af8f-3e7f-4576-9804-4aeb74efdf5f" />


Important NumPy operations:
1. np.random.normal()
2. np.cumprod()
3. np.insert()
4. np.mean()
5. np.std()
6. np.max()
7. np.min()
The calculates the final stock price, maximum and minimum price, total return, average daily return, and daily volatility.

_Step 2 — Portfolio Simulation_
Step 2 extends the stock-price simulation into an investment scenario. An initial investment of $10,000 is made when the simulated stock price is $100.

Number of shares:
shares = initial_investment / initial_price

This results in 100 shares. The model then calculates the final portfolio value, profit or loss, and portfolio return based on the simulated final stock price.

<img width="526" height="276" alt="Screenshot 2026-09-23 195724" src="https://github.com/user-attachments/assets/b5f3c1b2-3a33-4e18-8910-cb160e1d73d3" />


_Step 3 — Risk Analysis_
Step 3 introduces financial risk metrics to evaluate the simulated price path.

a. Maximum Drawdown:
Maximum drawdown measures the largest decline from a previous running peak.

running_max = np.maximum.accumulate(prices)

drawdown = (prices - running_max) / running_max

b. Sharpe Ratio:
A simplified annualized Sharpe ratio is calculated using the simulated mean return and volatility, with a 0% risk-free-rate assumption.

sharpe_ratio = (np.mean(random_returns) / np.std(random_returns)) * np.sqrt(252)

c. 95% Value at Risk:
A simplified historical-style VaR is estimated using the 5th percentile of simulated daily returns.

var_95 = np.percentile(random_returns, 5).

Additional risk metrics include the best trading day and worst trading day.

<img width="462" height="232" alt="Screenshot 2026-09-23 195705" src="https://github.com/user-attachments/assets/b57f7b4e-029e-4e32-b0f5-e60c0f3af1a3" />


_Step 4 — Monte Carlo Simulation_
Instead of generating one possible future, Step 4 generates 1,000 possible stock-price paths, with each path containing 252 trading days.

The return matrix therefore has the shape:(1000, 252)

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

<img width="576" height="430" alt="Screenshot 2026-09-23 201430" src="https://github.com/user-attachments/assets/9c3b5544-e3d9-446f-9f5f-198a3b1564fb" />


Final portfolio results from the completed simulation:

<img width="450" height="292" alt="Screenshot 2026-09-24 111149" src="https://github.com/user-attachments/assets/a0ea4ef2-a7ba-4a9b-8f03-cbb0d66847e3" />


These results describe the simulated distribution produced by the selected assumptions. They should not be interpreted as predictions of actual market outcomes.

E. Visualization 📊📈

Matplotlib is introduced for visual analysis. Two main visualizations were created.

E.1 Monte Carlo Stock Price Paths
The first chart displays 100 of the 1,000 simulated stock-price paths. All paths begin near the initial price and gradually spread as random daily returns accumulate.

<img width="712" height="393" alt="Screenshot 2026-09-23 202218" src="https://github.com/user-attachments/assets/2a86ff88-be42-4161-8880-1881b288c2bc" />

 
E.2 Distribution of Final Portfolio Values
The second chart is a histogram of the 1,000 final portfolio values. It includes reference lines for the initial investment, mean, and median, making it easier to compare the simulated outcomes with the starting $10,000 investment.

<img width="713" height="461" alt="Screenshot 2026-09-23 202844" src="https://github.com/user-attachments/assets/944ffb4c-2353-4387-aacf-13a5629bb3e5" />

F. Percentile & Scenario Analysis 💯

The final stage analyzes the distribution of final portfolio values using percentiles. Percentiles help describe different parts of the simulated outcome distribution.

<img width="507" height="197" alt="Screenshot 2026-09-23 204233" src="https://github.com/user-attachments/assets/50a56f6b-1ead-4302-bdd3-01ea798cd2df" />
<img width="458" height="198" alt="Screenshot 2026-09-23 204248" src="https://github.com/user-attachments/assets/34de6982-8443-44bb-8a29-5c643bcf8639" />
<img width="421" height="205" alt="Screenshot 2026-09-23 204309" src="https://github.com/user-attachments/assets/cd59d317-9827-4134-9a05-18512480dff3" />


These scenarios describe the simulated distribution under the model assumptions and are not forecasts.

G. Key NumPy Concepts Practiced 🔢

<img width="465" height="337" alt="image" src="https://github.com/user-attachments/assets/46408626-c5c9-4bf9-8cc3-447cc65491d8" />


H. Key Financial Concepts Practiced 💱

1. Daily returns
2. Stock-price simulation
3. Portfolio value
4. Profit and loss
5. Portfolio return
6. Volatility
7. Maximum drawdown
8. Sharpe ratio
9. Value at Risk (VaR)
10. Monte Carlo simulation
11. Simulated probability of profit/loss
12. Percentile analysis
13. Scenario analysis

I. Project Structure ⚙️

Stock-Price-Monte-Carlo-Simulator/
│
├── stock_simulator.py
├── README.md
├── requirements.txt
└── screenshots/
    ├── monte_carlo_price_paths.png
    └── portfolio_value_distribution.png

J. How to Run 👩‍💻

Install the required packages:
pip install numpy matplotlib

Then run the Python script:
python stock_simulator.py

The program prints the simulation statistics and generates the visualization charts.

K. Main Assumptions 💵

<img width="380" height="220" alt="image" src="https://github.com/user-attachments/assets/3323f404-2816-4833-b997-f3150af78f2c" />

for the simplified Sharpe-ratio calculation

L. Learning Outcome 🔳

This project demonstrates how Python and NumPy can be used to build a financial simulation from the ground up. It combines Python programming, numerical computing, statistics, finance, Monte Carlo simulation, risk analysis, and data visualization.
The project is particularly relevant for demonstrating practical skills in Finance, Business Analytics, Quantitative Analysis, and Python-based Data Analytics.

M. About 🙋‍♀️
Shrestha Sarkar
PGDM — Finance Major | Business Analytics Minor
Skills demonstrated: Python, NumPy, Matplotlib, Financial Analysis, Risk Analysis, Statistical Simulation, Monte Carlo Simulation, and Data Visualization.

N. License 📄

This project is licensed under the [MIT License](LICENSE).
