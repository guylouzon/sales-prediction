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





  

