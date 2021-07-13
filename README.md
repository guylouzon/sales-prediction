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


