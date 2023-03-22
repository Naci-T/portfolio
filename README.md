# Portfolio optimization and prediction

This project consists of two parts. The notebook portfolio_optimization_prediction.ipynb optimizes a portfolio and forecasts the future prices of this portfolio. The main portofolio optimisation.ipynb is the end product of the project but the methods in the predictions folder (predictions.ipynb, pycaret.ipynb) helped to choose the best method for the optimalisation of the project. 

## Part 1 - Portfolio optimization and prediction
### Introduction

Here comes general information about portfolio optimization (general explanation efficient frontier etc? )

HERE COMES FIGURE 

### Requirements

Make requirements .txt

### Usage 
After the functions there's an example of how to use the functions. It's advised to make a new function to test
several stocks. Here is an example of how to use the functions: 
- Enter the start and end dates for which you want to get the historical stock data.
- Enter the list of stocks you want to analyze.
- Use the `optimize_portfolio` function to optimize the portfolio based on the desired method ('sharpe' or 'risk').
- Use the `info` function to see the expected annual return, annual volatility, and Sharpe ratio of the portfolio.
- Use the `number_of_stocks_to_buy` function to get the number of stocks to buy with the given investment amount.
- Use the `pie_plot` function to create a pie chart showing the distribution of the portfolio weights.

Illustration of how the output looks when you plan to invest $ 10,000 in 8 stocks: 

<img title="graph" alt="graph" src="./images/example.png" width="800">

Here comes the prediction part!

##  Part 2 - Prediction of stock prices with xgboost and pycaret

requirements.txt

### Introduction

The notebooks [prediction.ipynb](./predictions/prediction.ipynb) and [pycaret.ipynb](./predictions/pycaret.ipynb) (in folder 'predictions') are mainly used to explore different methods in order to forecast future stock prices. The first one used 'xgboost' whereas the second notebook used the library pycaret which is suitable for people with less experience in machine learning.  

The main idea was to select the best method in order to use in the project [Optimalisation.ipynb](./Optimalisation.ipynb) above. The information below is only valid for the notebook [prediction.ipynb]. 

#### Data Retrieval and Preparation

In the first section of the notebook, we retrieve the adjusted closing prices for a list of stocks using Yahoo Finance API. We use the get_data() function to retrieve the data for a specified date range. We then use the prepare_data() function to prepare the data for modeling. In this function, we add lag to the data and split it into training and test sets.


#### Modeling 

We use XGBOOST to build a regression model to predict the stock price of Microsoft. First, we train an XGBOOST model with default parameters using XGBRegressor(). We then use a grid search to find the best hyperparameters for our model using GridSearchCV(). We search over the hyperparameters n_estimators, max_depth, and learning_rate.

After finding the best parameters using the grid search, we build our final XGBOOST model with the hyperparameters. We use XGBRegressor() to build the model with objective='reg:squarederror', n_estimators=500, early_stopping_rounds=50, learning_rate=0.01, and max_depth=7. 

We evaluate our model by computing the root mean squared error (RMSE) on the test set using mean_squared_error(). We compare the predicted values to the actual values by plotting them using matplotlib.


#### Prediction 

Finally, we predict the stock prices for the future 5 business days as from January 1st, 2023. We use the predict_head() function to make the prediction. Note that the predict_head() function will only predict the future 5 business days as from January 1st, 2023, and the function is hardcoded to use the best model we found earlier in the notebook. If you wish to make a prediction for a different date range, you will need to modify the function accordingly.

## Conclusion
This project shows how to optimize a portfolio and predict stock prices using different techniques. Feel free to modify the code and add more features to make it more useful for your needs. 

## Limitations

Here comes limitations


