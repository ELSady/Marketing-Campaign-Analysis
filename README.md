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


* Transfomring `Dt-Customer` to date feautre instead of string.

Creating `Age` feature
* This feature are based on the differentitaion of the year 2022 minus the `CUstomer YearBirth` feature. <br>


`Total Spend` feature
* The total soending acumulation includes how much the customer have spent on  Wines, Fruits, Meat Products, Fish Products, Sweet Products, and Gold Products`. <br>


`Purchase Frequency` feature
* This feature includes a total number of how frequent customer have spent on at the sotre. Purchases includes from web purchase, catalog or directly to the store. <br>


`Children` feature
* The total children for a given customer. <br>


### Desciptive Statistics


