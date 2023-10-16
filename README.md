# Univariate Time Series Analysis

## Description

This project intends to appropriately analyze and fit machine learning models to univariate time-series data, where we have the scanned receipts for every day of the year. The goal is to construct a model from the ground up that best minimizes mean squared errors, without using advanced libraries like `scikit-learn` or `keras`. The most advanced library implemented is `scipy`, specifically Nelder-Mead optimization, to fine-tune parameters that minimize mean squared errors.

First, we visualize the data by plotting the time series, seasonal, box, and decomposition plots to study seasonality and cyclic fluctuations for both day-wise and month-wise periods. The trend and seasonality are additive, with more or less constant variation. Furthermore, we also implement the Kruskal-Wallis statistical ANOVA test with a controlled error rate to rigorously argue the significance of seasonality for both day-wise and month-wise periods. Doing the above, we find the day-wise seasonality is negligible, whereas month-wise seasonality is statistically significant. Due to this, we move forward and use month-wise periods in our ML models going forward.

Next, we fit a Single Exponential Smoothing (SES) model to our data. Nelder-Mead non-gradient optimization algorithm is utilized to fine-tune and search for the smoothing parameter that minimizes mean forecast error, and we fit the smoothing curve to our data. We notice that the exponential smoothing matches very closely to our data. This is good as it implies that SES can capture short-term fluctuations well. However, there is the issue that it fits our data too well, not leaving any room for generality in making future predictions. To offset this, we derived and implemented linear regression (from scratch), which does not capture short-term fluctuations but can model long-term trends.

Finally, we used weights for the SES and Regression models. Nelder-Mead was implemented again to find the weights that minimize Mean Squared Error (MSE). This gave us a model that captured most short-term fluctuations and long-term trends while also leaving enough room for generality and prediction purposes.

**Note: It is highly suggested to run the jupyter notebook on docker as many of the plots are interactive. The instructions to run the docker file is given below.**

## Run jupyter notebook on [docker](https://hub.docker.com/repository/docker/stochastic1017/ml_time_series/general)

Make sure to have docker installed on your local machine, link to download can be found [here](https://www.docker.com/get-started/). 

### 1.) Pull this image using the provided command:

 ```
docker pull stochastic1017/ml_time_series
 ```

### 2.) Start the container:

Use the following command to start the container:

```
docker run -it -p 8888:8888 stochastic1017/ml_time_series
```

### 3.) Accessing Jupyter Notebook

The container prints the Jupyter kernel log into the terminal. Opening the link `http://127.0.0.1:8888/?token=...` in a browser opens the front end of the Jupyter server created by the container.

### 4.) Access ipynb file

After accessing Jupyter Notebook, click on project, the folder will contain the `data_daily.csv` as well as the `ML_Univariate_Time_Series.ipynb` file. Open this file to access the model used to analyze and forecast the time series dataset.

### 5.) Stopping the Container

Press `CTRL+C` in the terminal displaying the Jupyter Notebook kernel and confirm with `y`.

### 6.) Open Container Terminal

Executing `docker run` with this image will turn the terminal into the output of the Jupyter kernel, where you won't be able to enter further commands. If you want to look at the running containers, run

```
docker ps
```

Then execute the following command to get into a specific container

```
docker exec -it <container_name> /bin/bash
```

## Interactive Plots:

The html links to plots that are not rendered in the ipynb file are given below:

1. [Original Time Series Plot](https://htmlpreview.github.io/?https://github.com/Stochastic1017/Time-Series-Analysis/blob/main/html/Original_Time_Series_Data.html)
2. [Seasonal Plot of Receipt Count against Days](https://htmlpreview.github.io/?https://github.com/Stochastic1017/Time-Series-Analysis/blob/main/html/Seasonal_Plot_Receipt_Counts_Days.html)
3. [Seasonal Plot of Receipt Count against Months](https://htmlpreview.github.io/?[https://github.com/Stochastic1017/Predicting-Gender/blob/main/Images/PCA-3d.html](https://github.com/Stochastic1017/Time-Series-Analysis/blob/main/html/Seasonal_Plot_Receipt_Counts_Month.html))
4. [Single Exponential Smoothing (SES)](https://htmlpreview.github.io/?https://github.com/Stochastic1017/Time-Series-Analysis/blob/main/html/Single_Exponential_Smoothing.html)
5. [Scatterplot of time-series data](https://htmlpreview.github.io/?https://github.com/Stochastic1017/Time-Series-Analysis/blob/main/html/Scatter_Plot_Time_Series_Data.html)
6. [Scatterplot of time-series data with fitted regression trend line](https://htmlpreview.github.io/?https://github.com/Stochastic1017/Time-Series-Analysis/blob/main/html/Scatter_Plot_Time_Series_Data_Regression_Line.html)
7. [Weighted-Averaged Ensemble SES + Regression model](https://htmlpreview.github.io/?https://github.com/Stochastic1017/Time-Series-Analysis/blob/main/html/Ensemble_SES%2BReg_Model.html)
8. [Scatterplot with all models fitted for comparison](https://htmlpreview.github.io/?https://github.com/Stochastic1017/Time-Series-Analysis/blob/main/html/Scatter_Plot_All_Models_Fitted.html)
