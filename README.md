# sales-prediction
a python based time series segmentation and prediction for retail sales 


## Preface

This project  aims to predict online retails sales of a multi vendor store using machine  learnong techniques, in python language

The data used in this project is from an online multi  vendor store, located in Barzil, for the brazilian market, named Olist. Their data  of salea for the period of 01/2017 – 07/2018 the fully published on kaggle
https://www.kaggle.com/olistbr/brazilian-ecommerce
![image](https://user-images.githubusercontent.com/9468761/125505920-1279a18d-a986-4e9e-97e0-77950c62f922.png)


## Goal

Business issue to resolves:
recognizing the trend of revenues and product sales and prepare the appropriate budget

As a marketplace, we expect various trends to appear in the data, based on products, customers and sellers



## Given Data

customers = unique data per customer, mostly address data
Order items = order items details – the actual sales data
orders = data per order, mostly dates and delivery status
products = unique data per product , physical dimensions, and category
sellers = unique data per seller
Product category name translation = English to portugues naming

## Given

Most of the data in each table consists of very few features
Plotting is practically possible only when crossing it the sales data (order items), all of which, tends to look similar

As it seems, we’re going to need to slice the data at it’s edges as it looks not as complete as other months
We can also notice more volatility in 2018, which doesn’t appear in 2017
We’re going to have to do some feature engineering before we EDA

![image](https://user-images.githubusercontent.com/9468761/125506276-80434397-5b2a-4da7-a6fa-b129016c5d78.png)

## Preprocessing

Our anchor dataset is of order items over time, for each main object: product, customer or seller, we’ll join with order items, then group by the object, trying to get any extra information that we can

So, we got:
	The obvious: average sales, total sale count, total sales sum
	more: lifetime, age in the system
	trends: the sales amount per week, for the training period, is the object active (sold in the month), was the object selling more than or less than in the last month in comparison to the previous
  
  ![image](https://user-images.githubusercontent.com/9468761/125506399-fdc6ec10-3c8b-45eb-9880-7573f10bcce7.png)


## Analysis – time from the last sale/ purchase

The metric – the time past since the last sale and end of training period.
The more the distribution is closer to zero (less time) – the better:
	we have relatively a lot of new sellers
	we have an good enough variety of product sold
	we have a new customers issue…

![image](https://user-images.githubusercontent.com/9468761/125506531-b793db58-f497-4b1b-bce2-4b9bf20fcc22.png)


## Clustering

Now that we have built 6 new dataframes to work on, including numerous engineered columns, and looking into the assumption that there are various trends per product, customer and seller, we can cluster them.
I have used Kmeans to cluster, measuring the ideal number of them by distortion (elbow) and silhouette

for customer we'll choose 3 clusters, for sellers 3 as well and for products we can take 4.

After clustering for each object in separate – we can use the cluster of each 2 objects as features for clustering in the 3rd

![image](https://user-images.githubusercontent.com/9468761/125671292-4612b662-583d-4eca-9012-3197866299a9.png)


## Analysis – total sales count, per object, per cluster

The metric – the time past since the last sale and end of training period.
The more the distribution is closer to zero (less time) – the better:
	we have relatively a lot of new sellers
	we have an good enough variety of product sold
	we have a new customers issue…
	
![image](https://user-images.githubusercontent.com/9468761/125671370-ca827f9e-3e69-40b1-8fd0-0ab0bee2dbfa.png)


Quickly analyzing the data, after examining the distribution and graphs of a 3 clusters split for the sellers, we can see that some features are better split by cluster and some less so we can afford to take 6 clusters

![image](https://user-images.githubusercontent.com/9468761/125671424-d53c8ee1-b15a-4aec-b1cf-79bcccc48c9c.png)

## Feature engineering and clustering - summary

We got a robust set of dataframes to work with – which may enable us to conduct any number of valid predictions, either classifications or regression
 for time series we have the ability to predict, but:
We’re limited in the number of periods, we have only a year and a half worth of data
We have a big outlier case which is across the board, on a few days in Nov-17
Right in Jan-18, on the calendar year’s end, we have a huge drop that might effect the trend recognition

## Modeling

The time series model chosen for the project is Facebook prophet
The catches:
Prophet can predict for various time periods, we want a monthly resolution, but we loose granularity. We’ll attempt at daily then aggregate per month

The model only accepts a time series as an input: date stamp(ds) and y (the predicted variable)
Meaning we cannot pass the features directly, but rather indirectly – i.e after having quality clusters split the data
	this is limited since we cannot feature engineer the time trends on the test data: the trends at the end of 2017 are comparable to the trends of 2018 ?
	we’re going to check the quality of summarized data on the real test data

### Attempts

The outliers and jan-18 drop, makes it hard to predict the trend for 1-6/18 from the year of 2017, we must choose, under the current data limitations, either predicting using 1-11/17 data, or 1/17-1/18 data
Holidays don’t really help the model, they actually make it worse

### Methodology

Predict, for each object’s cluster, the future sales sum, and sales count
Aggregate all of the clusters to one final result
Average them all to receive the final result
We’d expect to see a different bias when predicting for customers, products and sellers, averaging through it, should help disable the bias

![image](https://user-images.githubusercontent.com/9468761/125671661-7968c388-9300-44e9-a52d-2db36cf591a9.png)


## Modeling – unique customers, sellers and products

Using the same methodology, of predicting using clusters, we predict the unique count of products, sellers and customers
Unlike before, there’s less point of averaging the different objects
The prediction quality is lower*

* Prophet has the ability to add a regressor to the prediction – in our case, the previous sales sum prediction, that might help adjust the results. I still have bugs in adding regressors

![image](https://user-images.githubusercontent.com/9468761/125671778-8c8172ef-7b83-4abc-b5ff-aa920a2e9291.png)

## results

The main predictive metrices have an upwards bias that derives from the outlier case, happening in test period. We have to big drops in 2018 that are also hard to predict, as intuitively predicted
Lack of more data prevented a more robust model

![image](https://user-images.githubusercontent.com/9468761/125671847-a3cb01b2-f4ac-4b44-8c0c-db559a4ebffe.png)




  

