# Udacity AWS Machine Learning Engineer Nanodegree Capstone project

## Domain Background

### Student briefly details background information of the domain from which the project is proposed. Historical information relevant to the project should be included. It should be clear how or why a problem in the domain can or should be solved. Related academic research should be appropriately cited. A discussion of the student's personal motivation for investigating a particular problem in the domain is encouraged but not required.

In sensitive markets, like Taiwan, regulators post a list of stocks daily that are deemed to have high execution risk that could lead to financial contagion due to their volatility (fast/significant price fluctuations) or because a particular account is trading a large majority of the daily volume of the security. So, Regulators require buys/sells of these securities to be pre-funded/delivered. The purpose of this project would be to use historical/current data as inputs to train a model to predict which securities will be flagged the next day at the close of trading on the current day in order to improve fund operations by being able to move money/securities around 12 hours in advance if portfolio managers plan on making a trade in one of these securities on market open the next day before prices move out of favor.  

In Taiwan the regulators are not completely specific as to the rules used, hence the need for an ML model that’s accessible through an API using attributes such as price fluctuation, PE ratio, price to book ratio, trading volume, and turnover as factors to retrieve their predictions.

## Problem Statement

### Student clearly describes the problem that is to be solved. The problem is well defined and has at least one relevant potential solution. Additionally, the problem is quantifiable, measurable, and replicable.

- The TWSE issues a daily "watch list" that identifies stocks where the price fluctuation, PE ratio, price to book ratio, trading volume, or turnover rate is too high. The problem is to predict on a daily basis, at the close of trading (T), which stocks will be placed on the watch list for the next day (T+1).  



- The risks of a false positive are that if the front office has an open order for the stock the following day, that a same-day (T0) FX is executed for the trade when it doesn't need to be. This may subsequently need to be reversed because the portfolios do not want to accept extra foreign-exchange rate risk. The larger the FX, the greater the risk, and the larger the TWD/USD exchange rate pair volatility, the greater the risk.  

- The risks of a false negative are that middle office must initiate a T+0 FX with the custodian but this will often not be settled until mid afternoon, then cash needs subsequently moved to the broker cash account. Often this will mean front office has effectively lost most of the equity trading day and if the order was marked to trade on the open we will have missed the benchmark by almost a full day. The higher the market value of the order, the larger the risk. The higher the volatility of the underlying stock, the larger the risk.  

- Qualitatively, the middle office has stated that the risks of a false negative are expected to be greater than the risks of a false positive, because in general the market opportunity cost is greater than the FX volatility. This is because in general, equity market volatility is greater than FX market volatility, and because typically the reason that a stock is placed on the watch list is due to market events which present a critical window of time in which to trade the stock.  

## Solution Statement

### Student clearly describes a solution to the problem. The solution is applicable to the project domain and appropriate for the dataset(s) or input(s) given. Additionally, the solution is quantifiable, measurable, and replicable.

- The solution should be a binary classification model.  The model must be able to perform batch predictions on a list of stocks within the investible universe of stocks listed in Taiwan.

- Because of the need to minimize the risk of false positives, the model should try to maximize recall, or the 'sensitivity'. This is calculated as (TP / (TP + TN)), where TP stands for 'True Positives' and TN stands for 'True Negatives'. Refer to this guide for more on [binary classification metrics]('https://towardsdatascience.com/the-explanation-you-need-on-binary-classification-metrics-321d280b590f')

## Datasets and Inputs

### The dataset(s) and/or input(s) to be used in the project are thoroughly described. Information such as how the dataset or input is (was) obtained, and the characteristics of the dataset or input, should be included. It should be clear how the dataset(s) or input(s) will be used in the project and whether their use is appropriate given the context of the problem.

- The dataset is split between two exchanges, the Taiwan Stock exchange and the Taipei stock exchange. To obtain the full universe we must combine both exchanges.
- Data can be obtained on [Taipei Stock Exchange website]('https://www.tpex.org.tw/web/stock/aftertrading/cmode/chtm.php?l=en-us') and the [Taiwan Stock Exchange website]('https://www.twse.com.tw/en/')
- Due to time constraints, we will train on the Taiwan Stock Exchange (TWSE) listed stocks.
- Data for these stocks have been downloaded from the website at the following links:  
    - "ratios" : 'https://www.twse.com.tw/en/page/trading/exchange/BWIBBU_d.html',
    - "short_sales" : 'https://www.twse.com.tw/en/page/trading/exchange/TWTASU.html',
    - "summary_px_vol" : 'https://www.twse.com.tw/en/page/trading/exchange/MI_INDEX.html#subtitle7',
    - "full_delivery": 'https://www.twse.com.tw/en/page/trading/exchange/TWT85U.html'
- Zipped files for each of these datasets from 1/1/2022 through 10/31/2022 are included in this repository as follows:
    - udacity-aws-machine-learning-nanodegree-capstone/taiwan-pe-pb-ratios-website-raw-01012022-10312022.zip
    - udacity-aws-machine-learning-nanodegree-capstone/taiwan-shortsale-data-website-raw-01012022-10312022.zip
    - udacity-aws-machine-learning-nanodegree-capstone/taiwan-summary-website-raw-01012022-10312022.zip
    - udacity-aws-machine-learning-nanodegree-capstone/taiwan-watchlist-data-website-raw-01012022-10312022.zip
    
## Benchmark Model

### A benchmark model is provided that relates to the domain, problem statement, and intended solution. Ideally, the student's benchmark model provides context for existing methods or known information in the domain and problem given, which can then be objectively compared to the student's solution. The benchmark model is clearly defined and measurable.

- No existing model exists by which to benchmark.
- The ML engineer intends to begin with a linear model, and one or more decision tree-based models (random forest, XGBoost), as well as more as they have time.

## Evaluation Metrics

### Student proposes at least one evaluation metric that can be used to quantify the performance of both the benchmark model and the solution model presented. The evaluation metric(s) proposed are appropriate given the context of the data, the problem statement, and the intended solution.
- The loss function should be based on l
- A baseline desired recall per the front office guidance would be a precision of 90-99% desired.

## Presentation

### The proposal follows a well-organized structure and would be readily understood by its intended audience. Each section is written in a clear, concise and specific manner. Few grammatical and spelling mistakes are present. All resources used and referenced are properly cited.

## Project Design

### Student summarizes a theoretical workflow for approaching a solution given the problem. A discussion is made as to what strategies may be employed, what analysis of the data might be required, or which algorithms will be considered. The workflow and discussion provided align with the qualities of the project. Small visualizations, pseudocode, or diagrams are encouraged but not required.