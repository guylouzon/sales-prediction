# Sales Prediction Project
> A Python-based time series segmentation and prediction system for retail sales

## 📌 Quick Links
- [GitHub Repository](https://github.com/GuyLou/sales-prediction/blob/main/olist-online-sales-prediction-time-series-forecast.ipynb)
- [Kaggle Notebook](https://www.kaggle.com/guylouzon/olist-online-sales-prediction-time-series-forecast)

## 🎯 Project Overview
This project implements machine learning techniques to predict online retail sales for a multi-vendor store. The analysis focuses on the Brazilian e-commerce platform Olist, using their sales data from January 2017 to July 2018.

![Olist Overview](https://user-images.githubusercontent.com/9468761/125505920-1279a18d-a986-4e9e-97e0-77950c62f922.png)

### Business Objectives
- Recognize revenue and product sales trends
- Prepare appropriate budget forecasts
- Analyze marketplace trends across products, customers, and sellers

## 📊 Dataset Description
The dataset includes multiple tables:
- **Customers**: Address and demographic data
- **Order Items**: Detailed sales transactions
- **Orders**: Order dates and delivery status
- **Products**: Physical dimensions and categories
- **Sellers**: Vendor information
- **Category Translation**: Portuguese to English mappings

### Data Characteristics
![Sales Distribution](https://user-images.githubusercontent.com/9468761/125506276-80434397-5b2a-4da7-a6fa-b129016c5d78.png)

Key observations:
- Limited features per table
- Similar patterns when cross-referenced with sales data
- Higher volatility in 2018 compared to 2017
- Edge data requires trimming for completeness

## 🔧 Methodology

### 1. Preprocessing
Created feature-rich datasets by:
- Joining order items with main objects (products, customers, sellers)
- Calculating key metrics:
  - Sales averages
  - Transaction counts
  - Customer lifetime value
  - System age
  - Weekly sales trends
  - Activity status

![Preprocessing Results](https://user-images.githubusercontent.com/9468761/125506399-fdc6ec10-3c8b-45eb-9880-7573f10bcce7.png)

### 2. Clustering Analysis
- Implemented KMeans clustering
- Determined optimal clusters using elbow method and silhouette scores
- Results:
  - Customers: 3 clusters
  - Sellers: 3 clusters
  - Products: 4 clusters

![Clustering Results](https://user-images.githubusercontent.com/9468761/125671292-4612b662-583d-4eca-9012-3197866299a9.png)

### 3. Time Series Modeling
Used Facebook Prophet with considerations for:
- Monthly vs daily resolution
- Limited feature engineering capabilities
- Outlier handling
- Holiday effects

![Modeling Results](https://user-images.githubusercontent.com/9468761/125671661-7968c388-9300-44e9-a52d-2db36cf591a9.png)

## 📈 Results

### Primary Findings
![Final Results](https://user-images.githubusercontent.com/9468761/125671847-a3cb01b2-f4ac-4b44-8c0c-db559a4ebffe.png)

- Upward bias in predictive metrics due to outlier cases
- Significant drops in 2018 affecting prediction accuracy
- Model limitations due to data availability

### Unique Entity Predictions
![Entity Predictions](https://user-images.githubusercontent.com/9468761/125671778-8c8172ef-7b83-4abc-b5ff-aa920a2e9291.png)

## 🔍 Future Improvements
- Implement regressor functionality in Prophet
- Gather additional historical data
- Enhance outlier handling
- Improve holiday effect modeling

## 📝 Notes
* Prophet's regressor capability could potentially improve results by incorporating sales sum predictions
* Current implementation has some limitations with regressor integration
