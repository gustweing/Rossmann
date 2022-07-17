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

The preparation of data will take place of this stage. It's mean use some methods to transform them.
It will be used "Rescaling Method" and "Transformation", wich contains the following steps: One Hot Encoding, Label Encoding, Ordinal Encoding and Nature Transform.

* Step 6 - Feature Selection

The Feature Selection step will to ocurr with the support of Boruta Algorythm. With it we will change the best features to use in our model. With this, we try to evoid the occurrence of overfiting.
In this point, we need use the knowledge gain with the EDA and mix it with the chosen features by Boruta. One of the biggest importance of EDA is showed here, where we mix the human knowledge about the business with the learning adquired by model. From that, the final columns will be chosed.  

* Step 7 - Machine Learning Model

How we are using a cyclic model, our objective is have one solution as fast as we could. Because of this we gonna use non complex models. In each cycle this Machine Learning listed can be changed, always trying to find the better one with the better results and using less computacional power. 
Here we will use five different kinds of Models:
1 - Average Model: This model is very important to serve as a parameter. This average model works like playing a coin, trying to guess a result.
2 - Linear Regression Model: Always using the concept of "ockham's razor", we need to try with a simple model. Using an simple model like Liner Regression, it means the data has linear features, so we can use more complex linear models.
3 - Linear Regression Regularized Model - Lasso: Always using the concept of "ockham's razor", we need to try with a simple model. Using an simple model like Liner Regression, it means the data has linear features, so we can use more complex linear models.
4 - Randon Forest - Are non-linear models, trying to model the complexity of the dataset.
5 - XGBoost Regressor - Are non-linear models, trying to model the complexity of the dataset.

![image](https://user-images.githubusercontent.com/83656797/178176479-c3666c5e-299e-45f4-8729-ffc428775be5.png)

The phenomenon that we are trying to model is a complex problem, so linear models will not work as well with this kind of problems. We will use a XGBoost for our official model in this cycle.

* Step 8 - Hyperparameter Fine Tuning

In this step are found the best paramethers for the XGBoost. Here an important choosen needs to be done. Focusing in CRISP model, we will optate by Randon Search model because the time that we have.

* Step 9 - Interpreting the errors

In this step we have the explanation about the models. For this project, we used three metrics:
MAE (Mean Absolute Error)
MAPE (Mean Absolute Percentage Error)
RMSE (Root Mean Squared Error)


MAE's characteristics:
Has te same weight for all errors. It means the value of error can be high ou low, all depends of business. It's a good metric for the business team. 

MAPE's characteristics:
It shows the average of error, in percentage. The model has the best behaviour with the value being lower. The MAPE has a big correlation with MAE's data because the porcentage showed by MAPE is based on value showed by MAE.
 
RMSE's characteristics:
If we have errors with outliers, it gets a lot of weight. The RMSE can be used to detail the upgrades that must be done in model. Aren't a good metric to be showed by Business Team. 

In this steps yet will be made the translation of the values of the model into real values for the CFO. 

* Step 10 - Publishing Model

The deploy will be made into a Heroku Cloud and be done an API request by Telegram's Bot.
Here the User will write the store's number and will see the value for the next six weeks.

![image](https://user-images.githubusercontent.com/83656797/179426690-24f7931f-4e03-4c5e-b5e3-6fda201f693d.png)


# 4.0 Top Insights
The main hypothesis found in EDA:

1 - Stores with bigger assortments should sell more.

**True**: Stores with bigger assortments really sells more then the others two types.

![image](https://user-images.githubusercontent.com/83656797/179421670-3eb526dc-3c74-473d-8b4e-188d47e6824f.png)


2 - Stores with more closest competitors shoul sell less.

**False**: There is no evidence that the fact that there are closer competitors will impact the fact of selling more or less.

![image](https://user-images.githubusercontent.com/83656797/179420557-9c745f99-60b4-40a2-b5ac-a6542fb36db7.png)


3 - Stores with activate promotions for a long time should sell more.

**False**: Store with promo activate for a long time sell less after some time.

![image](https://user-images.githubusercontent.com/83656797/179421580-bc70451b-65ec-40f4-a291-56310b35dd7f.png)


# 5.0 Conclusions

The model generate a Dataframe of each Store with the values foreseen separated in Worst Scenario, Best Scenario also with the MAE and MAPE statistics. From now on the CFO can see the value of each store for the next six weeks and make the best decisions from there.

![image](https://user-images.githubusercontent.com/83656797/179425903-9c2d9ad8-84ae-45ca-817b-4dfb5f9d7caf.png)

You can see how the Telegram's Bot works here: [Telegram's Bot](https://www.linkedin.com/feed/)  

# 7.0 Next Steps

For the next cicles some changes can be made. 
- Create new variables that can be important for the business;
- Collect more data trying maximize the performance;
- Try more complex Machine Learning Models;
- Collect feedback of CFO for maximize the performance;

# 8.0 Technologies

![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)

![PyCharm](https://img.shields.io/badge/pycharm-143?style=for-the-badge&logo=pycharm&logoColor=black&color=black&labelColor=green)

![Heroku](https://img.shields.io/badge/heroku-%23430098.svg?style=for-the-badge&logo=heroku&logoColor=white)

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
