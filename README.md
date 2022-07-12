## Data Science Project: Marketing Campaign Analysis Overview
* Dataset contains records of 2240 customers with their informations, their purchase / sales, and response for previous and the current campaign.
* Handling plus Feature Engineering several features, the likes of customer registered date, Age, Total Spending and Purchase Frequency.
* Visualize and Analyse customers's Relationship-Status, income Yearly and Education distribution, how each of these features correlates to total spending and response for current and prevous campaign.
* Visualize and Analyse customers response over the 5 past campaign.
* Build Supervised Machine learning Classification model, checking its feature importance and Shap value to determine which features contributes when it comes to predicting customer's response for the current campaign.


A marketing campaign is a comprehensive course of action to sell and promote something, either a product, service, or brand. In a marketing campaign, the team may have organized the promotion of goods through printed publications, radio, TV, billboards, banners, trade shows, conferences, online, and other kinds of media. Marketing campaigns promote products through different types of media, such as television, radio, print, and online platforms. Campaigns are not solely reliant on advertising and can include demonstrations, video conferencing, and other interactive techniques. Businesses operating in highly competitive markets and franchisees may initiate frequent marketing campaigns and devote significant resources to generating brand awareness and sales. 

### Business Questions:
* How is the customers response of current and over the past previous campaigns?
* How is the customers behaviour based on the available informations and how it relates to the campaign response?
* Which factor(s) contributes more in order for customer to give a positive feedback / response to the campaign?

### Project framework:
* Dataset Profiing
* Datasetr inspection, chceking for missing and anomaly values in dataset
* Dataset Cleaning, should there indeed be any missing / anomlay values, otherwise prooced straight to feature engineering
* Feature Engineering
* Exploratory Data Analysis
* Machine learning model building and implementation

### Packages Used:
* Pandas
* Numpy
* Matplotlib / Seaborn
* Scikit Learn
* Pycaret

### Dataset Profiling
* Datasetr consists of 2240 observations and 29 features with a total size of 64960.

* There are 24 missing values for `income` features. Because of the missing values do not exceed the threshold limit of 5% of a FIlling factor, we can choose to drop them. However, instead we will impute them, because at the end of the day, data is data and it is very valuable to just be dropped.

### Data Cleaning
* Here we impute the missing values using the tool from Scikit Learn.

* Checking for any anomaly values for categorical features. There were none.

* Cross chekcing for any missing values. Dataset is already cleansed.

### Feature Engineering
`Educationd` and `Marital-Status` Cardinality Handling. <br>



* This is the process we want to trim / reduce the cardinality of `Education` feature. Initially, there are 5 uniue values, we want to trim it down to just 2, due to the other 3 basically are includes in the first 2 ones, so the other 3 are redundant. This also applies to `Marital-Status` feature. Initially there are 8 unique values, we also want to trim it down toi just 2. SImilar to `Education` feature above, these other 6 values are redundant, and needs to be dropped. 

`Dt-Customer` Feaure Date Transformation. <br>


* Transforming `Dt-Customer` to date feautre instead of string.

`Age` feature
* This feature are based on the differentitaion of the year 2022 minus the `CUstomer YearBirth` feature. <br>


`Total Spend` feature
* The total soending acumulation includes how much the customer have spent on  Wines, Fruits, Meat Products, Fish Products, Sweet Products, and Gold Products`. <br>


`Purchase Frequency` feature
* This feature includes a total number of how frequent customer have spent on at the sotre. Purchases includes from web purchase, catalog or directly to the store. <br>


`Children` feature
* The total children for a given customer. <br>


### Desciptive Statistics

We can conclude form the above statistics:
* The average total spend of each customer customer is around 606 dollar. 
* Meanwhile average frequency purchases for each customer is around 13 times.
* Average income yearly for each customer is around 52238 dollar.

### Data Visualization
`Marital-Status` <br>

* 64% percent of customers are in married relationship, while the other 36 % percent categorised themselves as singles.
* Interestingly, non married customers are spending more than the married ones. To be precise, 13 dollars more than the average spedning of married customers. 620 dollars over 570 dollars.
* Whilst average spending for both categories are relatively the same. 13 times. 
* When it comes to campaign feedbacks, both also have similar things in mind. THe difference is, the amount who rejets the campaign are doubled for married one.

`Education` <br>

* 50 % percents of customers are undergraduate, 26 % percents have master degree, while 22 % have Doctoral and the rest of 2% are basics.
* The highest average spending out of 4 categories are oe who has the PhD status with average spending of 672 dollars, followed by undergraduate with 619 dollars, masters with 570 dollars and lastly, 81 dollars for ones who have basic degree.
* Average Purchase also has similar patterns as the above, with Phd status having the most frequet purchase out of 4 categories, but with a lesser degree of difference amongst 4, only 1 time separate them.
* For campaign feedback, this also exhibits siilar result to that of `Marital-Status` above, majority of customers do not give positive feedback to it.

`Income` <br>

* Seems the customers yearly income are prdominantly in the range of 50000. 
* When it comes to total spending custoomers with a higher income are likely to spend more at the store. Unfortunately, this is not always the case, because there are certain customers who have a very high income but only spend a little. These are the outliers.
* While for frequent spending higher income customers generally tend to spend more than the lsser ones. However, like the previous one, thiss is not always the case.

### Previous Campaign Overview


* In general, customer's reception of the campaigns proposed are not very well. Majority of times when the store proposes a certain campaign, many customers reject it, to be specific over 90% of them always reject the idea of a new proposal. The first campaign alone already rejected by the 94 % of customers. The second one is far far worse, with a whooping 99% of customers are in the oppsing side of the feedback. CLearly, the tore needs to improve how they handle or proporse something to customers. Marketing strategy needs to be improved.

### Supervised CLassification Modeling
* Using pycaret as a processing tool, we get the following:


### Model Building and Comparison


* Comparing and evaluating models performaces. Here we want to see the `AUC` score as a tool to compare and evaluate models. Due to the imbalanced nature of our dataset, `AUC` score is more precise and accurate than your regular `Accuracy` metric.
* One thing note aside from higher `AUC` core, we may wnat to look at and consider other factor, which is the time. Time refers to how long the model took to implement to dataset. As we can see above, Logistics Reegerssion indeed have the best for AUC, but the time needed are way way longer than any other models.
* SO based on that consideration we will use Random Forest, LGBM alongside Graident Boosting Classifier as a base models.

### Models Feature Importances
`LGBM Classifier` <br>

`Random Forest` <br>

`Gradient Boosting CLassifier` <br>


Insights we get from those 3 plots:
* 

