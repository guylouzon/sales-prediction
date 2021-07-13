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
![image](https://user-images.githubusercontent.com/9468761/125505971-509e8e58-5e77-46da-b8fa-b63ab3241146.png)


## Given Data

customers = unique data per customer, mostly address data
Order items = order items details – the actual sales data
orders = data per order, mostly dates and delivery status
products = unique data per product , physical dimensions, and category
sellers = unique data per seller
Product category name translation = English to portugues naming

Other data also exists, but not currently used
Since this is a timeseries for brazil, brazil Holidays were downloaded an set as well
![image](https://user-images.githubusercontent.com/9468761/125506064-b962f224-9856-4ee6-9825-d5983a86e5dc.png)
