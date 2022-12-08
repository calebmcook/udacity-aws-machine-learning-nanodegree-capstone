# Software Instructions
## Software used will include the below.
 - Amazon Sagemaker notebooks
 - Python, pandas, and other common open source libraries.
 - Selenium python library and the Google Chrome driver, which can be downloaded [here](https://sites.google.com/chromium.org/driver/?pli=1). Note: this is only required to scrape the data from the Taiwan Stock Exchange website. I have done that and provided the data already, with instructions below.
 - Amazon Forecast is an AWS Service that provides apis to train predictors and generate forecasts based on multiple algorithms, including ARIMA, Facebook Prophet, and DeepAR+, among others. It will select the best algorithm for each individual times series. Because this is a multivariate panel time series forecasting problem, Amazon Forecast was chosen as a best-in-class option. Alternates were considered including leveraging the DeepAR container within SageMaker, however, the time constraints and "undifferentiated heavy lifting" of that approach led me to choose Amazon Forecast service.

# Data Instructions
Data has been scraped from the source website, as described `propsal.md`. To utilize this, you may import .parquet files from `use_this_data` directory, or follow the steps provided in `01-EDA.ipynb` to generate a single dataframe.