# Udacity AWS Machine Learning Engineer Nanodegree Capstone project

## Domain Background

### Student briefly details background information of the domain from which the project is proposed. Historical information relevant to the project should be included. It should be clear how or why a problem in the domain can or should be solved. Related academic research should be appropriately cited. A discussion of the student's personal motivation for investigating a particular problem in the domain is encouraged but not required.

In sensitive markets, like Taiwan, regulators post a list of stocks daily that are deemed to have high execution risk that could lead to financial contagion due to their volatility (fast/significant price fluctuations) or because a particular account is trading a large majority of the daily volume of the security. So, Regulators require buys/sells of these securities to be pre-funded/delivered. The purpose of this project would be to use historical/current data as inputs to train a model to predict which securities will be flagged the next day at the close of trading on the current day in order to improve fund operations by being able to move money/securities around 12 hours in advance if portfolio managers plan on making a trade in one of these securities on market open the next day before prices move out of favor.  

In Taiwan the regulators are not completely specific as to the rules used, hence the need for an ML model that’s accessible through an API using attributes such as price fluctuation, PE ratio, price to book ratio, trading volume, and turnover as factors to retrieve their predictions.

## Problem Statement

### Student clearly describes the problem that is to be solved. The problem is well defined and has at least one relevant potential solution. Additionally, the problem is quantifiable, measurable, and replicable.

- The TWSE issues a daily "watch list" that identifies stocks where the price fluctuation, PE ratio, price to book ratio, trading volume, or turnover rate is too high. The problem is to predict on a daily basis, at the close of trading (T), which stocks will be placed on the watch list for the next day (T+1).  

- The solution should be a binary classification model  

- The risks of a false positive are that if the front office has an open order for the stock the following day, that a same-day (T0) FX is executed for the trade when it doesn't need to be. This may subsequently need to be reversed because the portfolios do not want to accept extra foreign-exchange rate risk. The larger the FX, the greater the risk, and the larger the TWD/USD exchange rate pair volatility, the greater the risk.  

- The risks of a false negative are that middle office must initiate a T+0 FX with the custodian but this will often not be settled until mid afternoon, then cash needs subsequently moved to the broker cash account. Often this will mean front office has effectively lost most of the equity trading day and if the order was marked to trade on the open we will have missed the benchmark by almost a full day. The higher the market value of the order, the larger the risk. The higher the volatility of the underlying stock, the larger the risk.  

- Qualitatively, the middle office has stated that the risks of a false negative are expected to be greater than the risks of a false positive, because in general the market opportunity cost is greater than the FX volatility. This is because in general, equity market volatility is greater than FX market volatility, and because typically the reason that a stock is placed on the watch list is due to market events which present a critical window of time in which to trade the stock.  

- Because of the need to minimize the risk of false positives, the model should try to maximize recall, or the 

## Solution Statement

### Student clearly describes a solution to the problem. The solution is applicable to the project domain and appropriate for the dataset(s) or input(s) given. Additionally, the solution is quantifiable, measurable, and replicable.

## Datasets and Inputs

### The dataset(s) and/or input(s) to be used in the project are thoroughly described. Information such as how the dataset or input is (was) obtained, and the characteristics of the dataset or input, should be included. It should be clear how the dataset(s) or input(s) will be used in the project and whether their use is appropriate given the context of the problem.

## Benchmark Model

### A benchmark model is provided that relates to the domain, problem statement, and intended solution. Ideally, the student's benchmark model provides context for existing methods or known information in the domain and problem given, which can then be objectively compared to the student's solution. The benchmark model is clearly defined and measurable.

## Evaluation Metrics

### Student proposes at least one evaluation metric that can be used to quantify the performance of both the benchmark model and the solution model presented. The evaluation metric(s) proposed are appropriate given the context of the data, the problem statement, and the intended solution.

## Presentation

### The proposal follows a well-organized structure and would be readily understood by its intended audience. Each section is written in a clear, concise and specific manner. Few grammatical and spelling mistakes are present. All resources used and referenced are properly cited.

## Project Design

### Student summarizes a theoretical workflow for approaching a solution given the problem. A discussion is made as to what strategies may be employed, what analysis of the data might be required, or which algorithms will be considered. The workflow and discussion provided align with the qualities of the project. Small visualizations, pseudocode, or diagrams are encouraged but not required.