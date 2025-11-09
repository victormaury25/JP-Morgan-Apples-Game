# JP-Morgan Apples Game 

This project is a challenge organized by the JPM ATS team at Imperial College on 29/10/2025. The goal was to predict the price of UK Apples using the price of German Apples and the EUR/GBP exchange rate, and to implement a trading strategy based on these predictions.

## Overview
We were provided with a CSV file containing:
- UK Apple prices (in GBP)
- German Apple prices (in EUR)
- EUR/GBP exchange rates

It was specified that the German prices follow a **Random Walk process**, while the **basis** (difference between UK and German prices in GBP) follows an **Ornstein-Uhlenbeck (OU) process**.

## Methodology
1. **Estimate OU process parameters:**  
   Using OLS regression on the basis to estimate mean reversion speed, long-term mean, and volatility.

2. **Estimate Random Walk parameters:**  
   Compute the daily increments of German prices to estimate drift and volatility.

3. **Predict UK Prices:**  
   Using the OU and Random Walk parameters, simulate the expected UK price for the next day based on current day information.

## Trading Strategy
- Go **long** if the predicted UK price is higher than today's price.
- Go **short** if the predicted UK price is lower than today's price.

> **WARNING** This strategy is probabilistic and may be highly volatile. Some periods may generate significant gains, while others may result in losses. Running the simulation multiple times may result in very different outcomes.

## Future Work
- Extend strategy to trade on the spread rather than just predicted price direction.  
- Implement hedging strategies using estimated OU and Random Walk parameters.  
- Explore risk-adjusted position sizing and volatility control.
  
## Usage
1. Clone the repository.
2. Ensure the `apples_exercise.csv` file is in the same folder as the notebook.
3. Open and run `JP-Morgan-Apples-Game.ipynb` in Jupyter Notebook.

