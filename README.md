# Rossmann

![image description](https://repository-images.githubusercontent.com/476548139/91c3cfaa-74ce-4d0a-a349-b787451cc54c)

# 1.0 Business Problem

This project is based in a Kaggle Challenge with a simulate business problem.
Rossmann is one of the largests drugstore in Europe. They operates over 3,000 drug stores in 7 European countries. 

In this challenge the CFO was needing renovate the stores, and for this he needs to know what is his budget to spend in each store. With this in mind, we will predict the sells value of each store for the next six weeks. 

This dataset has the following Features:

<details>
<summary>Features Descriptions</summary>

| Attribute | Description |
| :----- | :----- |
| id | An Id that represents a (Store, Date) duple within the test set |
| Store | Date of the home sale |
| Sales | The turnover for any given day |
| Customers | The number of customers on a given day |
| Open | An indicator for whether the store was open: 0 = closed, 1 = open |
| StateHoliday | Indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. |
| SchoolHoliday | Indicates if the (Store, Date) was affected by the closure of public schools |
| StoreType | Differentiates between 4 different store models: a, b, c, d |
| Assortment | Describes an assortment level: a = basic, b = extra, c = extended |
| CompetitionDistance | Distance in meters to the nearest competitor store |
| CompetitionOpenSince[Month/Year] | Gives the approximate year and month of the time the nearest competitor was opened |
| Promo | Indicates whether a store is running a promo on that day |
| Promo2 | Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating |
| Promo2Since[Year/Week] | Describes the year and calendar week when the store started participating in Promo2 |
| PromoInterval | describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store |

 </details>
 
 The dataset can be found in this link:
 
 [Dataset](https://www.kaggle.com/competitions/rossmann-store-sales)  
 
 
 The resolution of all problems bellow can be found in this notebook:
 
 [NOTEBOOK]()

# 2.0 Business Assumptions

We follow with the next assumptions:

- The days that stores were closed was not considered.
- For the stores with null value in "competitor_distance" we consider that it had no close competitors. For the reason that feature have importance, we full the null data with the distance 200.000m. This distance is longer enought to don't to harm the real data. 
- Our dataset has data of 1115 stores, with the first day being 2013-01-01 untill 2015-07-31.


# 3.0 Solution Development

For this problem we use the method called CRISP, which consists of completing a cycle trying to generate value in the fastest way.
Ten steps were used to tackle the problem, going through description, model selection, model usage and cloud publishing.
All datasets were collected in Kaggle, so it was not necessary to use a database to extract them.
In the end of project will be created an API to use like a Telegram Bot. In it the value will be shown as you chose the store.

* Step 1 - Data Description

This steps is where you have the first contact with the data. It will be checked the dimensions, details about the empty lines and filling them.
The Descriptive Statistics will be generate in this step, being divided in:

Central Tendency - Mean and Median;
  
Dispersion Tendency - Std, min, max, range, skew and kurtosis
 
* Step 2 - Feature Engineering

The main hypotheses will be created. Together with them new attributes will be created to add them in Dataset.

* Step 3 - Variable Filtering

As said in '2.0 Business Assumptions', the stores closed won't be used. In this step they goin to be deleted.

* Step 4 - EDA (Exploratory Data Analysis)

The EDA has an important role in project. It's through it we gain experience about the business, we validate our hypothesis and discover important features for the future model.
Will be used three different analysis.
1 - Univariate Analysis
2 - Bivariate Analysis
3 - Multivariate Analysis

Each one has their importancy and function. 
In Univariate will be checked the limits of each variable, bivariate will se how they comport with our response variable and multivariate will see the correlation between them. 

* Step 5 - Data Preparation

* Step 6 - Feature Selection

* Step 7 - Machine Learning Model

* Step 8 - Hyperparameter Fine Tuning

* Step 9 - Interpreting the errors

* Step 10 - Publishing Model

# 4.0 Top Insights

# 5.0 Business Results

# 6.0 Conclusions

# 7.0 Next Steps

# 8.0 Technologies
