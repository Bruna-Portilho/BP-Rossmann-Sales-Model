# BP-Rossmann-Sales-Model
This is a sales prediction machine learning project for Rossmann Drug Stores

![sales-prediction-social-media](https://user-images.githubusercontent.com/85244180/135611366-dbfb5c66-91fc-4922-ba8e-836b1703b284.png)
# Business problem
The CFO of Rossmann Drug Stores requested a sales predction for each store for the next six weeks in order to define a budget for stores renovation. The current prediction was not satisfactory as there were several inconsistencies. In this context, I developed a machine learning model in order to provide more accurately forecast store sales.
# Business Assumptions
- The days when stores were closed were removed from the analysis.
- Only stores with sales values bigger than 0 were considered.
- For stores which did not have Competition Distance information, it was considered that the distance should be two times bigger than the bigger distance from the nearest competitor.
# Attribute List
- Id - an Id that represents a (Store, Date) duple within the test set
- Store - a unique Id for each store
- Sales - the turnover for any given day (this is what you are predicting)
- Customers - the number of customers on a given day
- Open - an indicator for whether the store was open: 0 = closed, 1 = open
- StateHoliday - indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None
- SchoolHoliday - indicates if the (Store, Date) was affected by the closure of public schools
- StoreType - differentiates between 4 different store models: a, b, c, d
- Assortment - describes an assortment level: a = basic, b = extra, c = extended
- CompetitionDistance - distance in meters to the nearest competitor store
- CompetitionOpenSince[Month/Year] - gives the approximate year and month of the time the nearest competitor was opened
- Promo - indicates whether a store is running a promo on that day
- Promo2 - Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating
- Promo2Since[Year/Week] - describes the year and calendar week when the store started participating in Promo2
- PromoInterval - describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store
# Solution Strategy
The method used for the project was CRISP-DS, apply as the steps below:

**Step 01**. **Data Description:** The goal is to use statistical metrics to identify outliers in the business scope and also analyze basic statistical metrics such as: mean, median, maximum, minimum, range, skew, curtosis and standard deviation.

**Step 02**. **Feature Engineering**: The goal of this step is to obtain new attributes based on the original variables, in order to better describe the phenomenon to be modeled.

**Step 03**. **Data Filtering**: The goal of this step it to filter rows and delete columns that are not relevant for the model or are not part of the business scope.

**Step 04**. **Exploratory Data Analysis**: The goal of this step is to explore the data to find insights and better understand the impact of variables on model learning.

**Step 05**. **Data Preparation**: The goal of this step is to prepare the data prepare data for application of the machine learning model.  

**Step 06**. **Feature Selection**: The goal of this step is to select the better attributes to train the model. It was used Boruta Algorithm to make the selection.

**Step 07**. **Machine Learning Modeling**: The goal of this step is to do the machine learning model training.

**Step 08**. **Hyperparameter Fine Tunning**: The goal of this step is to choose the best values for each of the parameters of the model selected in the previous step.

**Step 09**. **Convert model performance to business values**:  The goal of this step is to convert model performance to a business result.

**Step 10**. **Deploy Model to Production**: The goal of this step is to publish the model in a cloud environment so that other people or services can use the results to improve the business decision. The cloud application platform choosed was Heroku.

**Step 11**. **Telegram Bot**: The goal of this step is to create a bot on the telegram app, that make possible to consult the forecast at any time.

# Top Three Data Insigths
**H1**: Stores with larger assortments should sell more.

**FALSE**: Stores with a larger assortment sell LESS.

![image](https://user-images.githubusercontent.com/85244180/135637281-5f0d6160-e245-49e8-8f3d-f1dbccba12ea.png)

**H9**: Stores should sell more over the years.

**FALSE**: Stores sell less over the years.

![image](https://user-images.githubusercontent.com/85244180/135638046-9dd85666-fa4e-4b6f-8caa-7549a5903de3.png)

 **H11**: Stores should sell more after the 10th of each month.
 
**TRUE**: Stores sell more after the 10th of each month.

![image](https://user-images.githubusercontent.com/85244180/135639149-69db891d-ba66-465f-b732-54f58909d312.png)

# Tested Machine Learning Models 

- Average Model
- Linear Regression Model
-  Linear Regression Regularized Model (Lasso)
-  Random Forest Regressor
-  XGBoost Regressor

# Machine Learning Models Performance

![image](https://user-images.githubusercontent.com/85244180/135642546-f625a607-a1c8-45bd-b4f5-b2432fff6915.png)


# Machine Learnig Performance after Hyperparemeter Fine Tuning

![image](https://user-images.githubusercontent.com/85244180/135654921-1fa910a1-a495-4036-bd7b-54d2569461d3.png)

Although the Random Forest Regressor Model presented better performance, this model usually requires a large amount of space on the server in deploy step, generating a significant cost increase for the company. Therefore, it was choosen the XGBoost Regressor Model, which after the hyperparameter fine tuning presented similar performance and requires less space on the server, generating a lower cost for the company.

# Model performance vs Business values

In addition to overall sales prediction, it was also calculated the sales prediction for the worst and the best scenario.

**Model with XGBoost Regression**

![image](https://user-images.githubusercontent.com/85244180/135664880-e12bf17c-49ae-4eed-a285-32d51e0508d8.png)

# How to access the prediction
## Pre-requirement

- Sign up Telegram and create an account

# Telegram
- To acess the predictions on Telegram, click in the below:

[<img alt="Telegram" src="https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white"/>]( https://t.me/rossmann_brunasdp_bot)

# How to get the prediction
- Send the store number (one each time) and get the sales prediction for the next six weeks.
- If the store number does not exist, it will get as an answer the message: "Store Not Available".

![image](https://user-images.githubusercontent.com/85244180/135685816-8bb3bacf-3795-4893-966a-c2e75d8e0846.png)

# Conclusion

Considering the first CRISP-DS cycle, the final model presented a usefull performance, considering the MAPE (Mean Absolute Percentage Error) of 0.11. However, for some stores, higher MAPE values were observed, such as 0.37 and 0.52, but this is a point that could be improved in the next CRISP cycle.

# Technologies
- Jupyter notebook
- Python

# Deploy into production
- Back end: Heroku
- Front end web: Telegram
- Database: Kaggle

# Author
Bruna Santiago Dias Portilho

[<img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>]( https://www.linkedin.com/in/bruna-portilho-b48309124)

