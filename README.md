# Univariate Time Series Analysis

## Run jupyter notebook on [docker](https://hub.docker.com/repository/docker/stochastic1017/ml_time_series/general)

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
