## Data Science Project: Marketing Campaign Analysis Overview
* Dataset contains records of 2240 customers with their informations, their purchase / sales, and response for previous and the current campaign.
* Handling plus Feature Engineering several features, the likes of customer registered date, Age, Total Spending and Purchase Frequency.
* Visualize and Analyse customers's Relationship-Status, income Yearly and Education distribution, how each of these features correlates to total spending and response for current and prevous campaign.
* Visualize and Analyse customers response over the 5 past campaign.
* Build Supervised Machine learning Classification model, checking its feature importance and Shap value to determine which features contributes when it comes to predicting customer's response for the current campaign.

![strategi-marketing-campaign](https://user-images.githubusercontent.com/96014656/178617542-ea98e1a0-9a32-43ff-8537-71cf8ccb0c37.jpg) <br>

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
* Dataset consists of 2240 observations and 29 features with a total size of 64960. <br>

![Screenshot 2022-07-13 at 06-24-36 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178615921-fb7b285e-3c0f-457b-8c00-263476de0a7e.png)

* There are 24 missing values for `income` features. Because of the missing values do not exceed the threshold limit of 5% of a FIlling factor, we can choose to drop them. However, instead we will impute them, because at the end of the day, data is data and it is very valuable to just be dropped. <br>

![Screenshot 2022-07-13 at 06-25-43 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178615959-d83c6105-1b86-4f04-bb89-7b1f7922aa44.png)

### Data Cleaning
* Here we impute the missing values using the tool from Scikit Learn. <br>

![Screenshot 2022-07-13 at 06-27-06 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616050-e4fcb36d-5da7-4262-8aa7-6103e50e8f89.png)

* Checking for any anomaly values for categorical features. There were none. <br>

![Screenshot 2022-07-13 at 06-26-46 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616084-ba471166-ba64-4cf9-8afe-e363c14ba179.png)

* Cross chekcing for any missing values. Dataset is already cleansed. <br>

![Screenshot 2022-07-13 at 06-27-37 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616114-69feff32-92f3-45d5-8ed4-3d8a6e64cc30.png) <br>

### Feature Engineering
`Educationd` and `Marital-Status` Cardinality Handling. <br>

![Screenshot 2022-07-13 at 06-28-11 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616572-9227e295-0b50-4c8e-b810-2f0777a9f23e.png)

* This is the process we want to trim / reduce the cardinality of `Education` feature. Initially, there are 5 uniue values, we want to trim it down to just 2, due to the other 3 basically are includes in the first 2 ones, so the other 3 are redundant. This also applies to `Marital-Status` feature. Initially there are 8 unique values, we also want to trim it down toi just 2. SImilar to `Education` feature above, these other 6 values are redundant, and needs to be dropped. 

`Dt-Customer` Feaure Date Transformation. <br>

![Screenshot 2022-07-13 at 06-28-38 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616593-92dc44d6-517f-48e4-8d79-45d7cb823657.png)

* Transforming `Dt-Customer` to date feautre instead of string.

`Age` feature <br>

![Screenshot 2022-07-13 at 06-28-52 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616618-1f7283e1-453c-4278-a9cb-b341bb386c0b.png)

* This feature are based on the differentitaion of the year 2022 minus the `CUstomer YearBirth` feature. <br>

`Total Spend` feature <br>

![Screenshot 2022-07-13 at 06-29-41 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616659-853e1e48-9de9-4c8f-94a0-feedf1194e35.png)

* The total soending acumulation includes how much the customer have spent on  Wines, Fruits, Meat Products, Fish Products, Sweet Products, and Gold Products. <br>

`Purchase Frequency` feature <br>

![Screenshot 2022-07-13 at 06-29-51 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616740-f816be6d-5802-443e-8f09-0f2cff391a1f.png)

* This feature includes a total number of how frequent customer have spent on at the sotre. Purchases includes from web purchase, catalog or directly to the store. <br>

`Children` feature <br>

![Screenshot 2022-07-13 at 06-30-06 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616754-884fd423-e424-4854-b3f1-fc72d22a081c.png)

* The total children for a given customer. <br>

### Desciptive Statistics

![Screenshot 2022-07-13 at 06-31-22 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616782-d7073a47-94b8-4a4c-8b57-1cd1b3ef0e71.png)

We can conclude form the above statistics:
* The average total spend of each customer customer is around 606 dollar. 
* Meanwhile average frequency purchases for each customer is around 13 times.
* Average income yearly for each customer is around 52238 dollar.

### Data Visualization
`Marital-Status` <br>

![index](https://user-images.githubusercontent.com/96014656/178616788-1a6dc14b-9c80-499a-9e6b-8cff3f69fc2d.png)

* 64% percent of customers are in married relationship, while the other 36 % percent categorised themselves as singles.
* Interestingly, non married customers are spending more than the married ones. To be precise, 13 dollars more than the average spedning of married customers. 620 dollars over 570 dollars.
* Whilst average spending for both categories are relatively the same. 13 times. 
* When it comes to campaign feedbacks, both also have similar things in mind. THe difference is, the amount who rejets the campaign are doubled for married one.

`Education` <br>

![index2](https://user-images.githubusercontent.com/96014656/178616809-ec183619-5876-4777-a6f6-827e1ae4db6e.png)

* 50 % percents of customers are undergraduate, 26 % percents have master degree, while 22 % have Doctoral and the rest of 2% are basics.
* The highest average spending out of 4 categories are oe who has the PhD status with average spending of 672 dollars, followed by undergraduate with 619 dollars, masters with 570 dollars and lastly, 81 dollars for ones who have basic degree.
* Average Purchase also has similar patterns as the above, with Phd status having the most frequet purchase out of 4 categories, but with a lesser degree of difference amongst 4, only 1 time separate them.
* For campaign feedback, this also exhibits siilar result to that of `Marital-Status` above, majority of customers do not give positive feedback to it.

`Income` <br>

![index3](https://user-images.githubusercontent.com/96014656/178616818-cedd48d4-b595-4212-9587-4447fb25a9fc.png)

* Seems the customers yearly income are prdominantly in the range of 50000. 
* When it comes to total spending custoomers with a higher income are likely to spend more at the store. Unfortunately, this is not always the case, because there are certain customers who have a very high income but only spend a little. These are the outliers.
* While for frequent spending higher income customers generally tend to spend more than the lsser ones. However, like the previous one, thiss is not always the case.

### Previous Campaign Overview

![index4](https://user-images.githubusercontent.com/96014656/178616832-8921506a-ec59-40ae-bca6-6f31f979193b.png)

* In general, customer's reception of the campaigns proposed are not very well. Majority of times when the store proposes a certain campaign, many customers reject it, to be specific over 90% of them always reject the idea of a new proposal. The first campaign alone already rejected by the 94 % of customers. The second one is far far worse, with a whooping 99% of customers are in the oppsing side of the feedback. CLearly, the tore needs to improve how they handle or proporse something to customers. Marketing strategy needs to be improved.

### Supervised Classification Modeling
* Using pycaret as a processing tool, we get the following: <br>

![Screenshot 2022-07-13 at 06-32-01 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616856-33e0eedf-c251-4849-bbcc-3187b0440a87.png)

### Model Building and Comparison

![Screenshot 2022-07-13 at 06-32-12 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178616865-803fdac4-50f7-47fe-9b69-ed0906b4d611.png)

* Comparing and evaluating models performaces. Here we want to see the `AUC` score as a tool to compare and evaluate models. Due to the imbalanced nature of our dataset, `AUC` score is more precise and accurate than your regular `Accuracy` metric.
* One thing note aside from higher `AUC` core, we may wnat to look at and consider other factor, which is the time. Time refers to how long the model took to implement to dataset. As we can see above, Logistics Reegerssion indeed have the best for AUC, but the time needed are way way longer than any other models.
* SO based on that consideration we will use Random Forest, LGBM alongside Graident Boosting Classifier as a base models.

### Models Feature Importances
`LGBM Classifier` <br>

![index5](https://user-images.githubusercontent.com/96014656/178616888-e60a9822-a89b-4375-8dd9-d4cb348b1ffd.png) <br>

`Random Forest` <br>

![index6](https://user-images.githubusercontent.com/96014656/178616902-11bc0526-28a7-4f8d-a3be-7a096f1a971a.png) <br>

`Gradient Boosting CLassifier` <br>

![index7](https://user-images.githubusercontent.com/96014656/178616912-1e61f51e-4714-4f60-ae38-18d111a83094.png) <br>

Insights we get from those 3 plots include:
* 3 classification modles above agree uppon the top 3 features which contributes the most when it comes to current campaign response.
* The 3 top features are `Total Spend`,`Recency` and `Income`. Not in order.
* We may want to further look how those 3 features affects the response / feedback outcome, Shapley plot can assits us to determine it.

### Model Interpretation
`LGBM` Shap Plot <br>

![index8](https://user-images.githubusercontent.com/96014656/178616930-84a1fd89-9d2f-4c17-8625-7e2c994ddd58.png) <br>

`Random Forest` Shap Plot <br>

![index9](https://user-images.githubusercontent.com/96014656/178616937-69c1b806-8702-48ef-8c62-c856060dc440.png) <br>

Insights we can get:
* A higher income customers have a high and positive impacts on campaign response feedback (Yes response).
* Similarly a higher total spend from customers also have a high and positive impact on campaign feedback.
* Meanwhile Recency opposite to the 2 features above, a higher value of Recency will have a negative impact on campaign response (No response).

### Choosing Best Modles and  Predict it on Hold out / Test Set

![Screenshot 2022-07-13 at 06-49-04 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178617109-c2ab775c-48a6-4fbf-a9e3-75c07acfeaef.png)

* Well use hyperparameter-tuned LGBM classificatio model and implement it to test set.

![Screenshot 2022-07-13 at 06-33-31 Marketing Campaign Analysis - Jupyter Notebook](https://user-images.githubusercontent.com/96014656/178617055-5e2df298-976d-4c1a-8698-1db7f0b157ce.png)

* Very good, the model retains its high score of `AUC` of 0.87. This is the model we are going to use for upcoming / future data.

### Conclusion
* Customers response for the propposed new campaign are not in a good shape. Of the 5 previous campaign proposed, majority customers reject them. One proposed campaign even have the 99% of customers reject the new idea. Store desperately needs new and appropriate marketing strategy or simply give the customers better proposal campaign.
* Average Spending for all customers is around 606 dollars, meanwhile average frequent purhase is around 13 times and lastly average yearly income is around 52238 dollars.
* 64 % of customers are married whilst the other 36 % are single. Non married customers are spending more than the married ones. Whilst average spending for both categories are relatively similar, 13 times. When it comes to campaign feedbacks, both also have similar things in mind.
* 50 % percents of customers are undergraduate, 26 % percents have master degree, while 22 % have Doctoral and the rest of 2% are basics. The highest average spending out of 4 categories are one who has the PhD status followed by undergraduate, masters with 570 dollars and lastly ones who have basic degree. Average Purchase also has similar patterns as the above, with Phd status having the most frequet purchase out of 4 categories. For campaign feedback, this also exhibits siilar result to that of `Marital-Status` above, majority of customers do not give positive feedback to it.
* Customers yearly income are predominantly in the range of 50000. Custoomers with a higher income are likely to spend more at the store. Unfortunately, this is not always the case, because there are the outliers. While for frequent spending higher income customers generally tend to spend more than the lsser ones. However, like the previous one, thiss is not always the case.
* From model interpretation, a higher income customers have a high and positive impacts on campaign response feedback (Yes response). Similarly a higher total spend from customers also have a high and positive impact on campaign feedback. Meanwhile Recency opposite to the 2 features above, a higher value of Recency will have a negative impact on campaign response (No response).
