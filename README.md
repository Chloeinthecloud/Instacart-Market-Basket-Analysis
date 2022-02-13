# Instacart-Market-Basket-Analysis
Instacart is an American technology company, which was founded in 2012. It operates as a same-day grocery delivery and pick-up service in US and Canada.
Customers could shop for groceries through Instacart App or Instacart.com from various retailer partners. The order is shopped and delivered by the Instacart Shoppers.

Here are the objectives of the project:

* Analyze the anonymized data of 3 million grocery orders from more than 200,000 Instacart users open sourced by Instacart
* Find out hidden association between products for better cross-selling and upselling
* Perform customer segmentation for targeted marketing and anticipate customer behavior
* Build a Machine Learning Model to perdict which previously purchased product will be in user's next order

## Project Organization
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/project%20organization.png)

## Data Description
* aisles: In this file, there are total 134 different aisles and aisles_id.
* departments: This file contains different departments and there are total 21 unique departments.
* orders: It contains all the orders made by different users. Based on the analysis, we can get the folowing conclusion:
   * There are total 3421083 orders made by 206209 different users.
   * Prior, Train and Test are three different sets of orders. The distribution of orders in Train and Test sets are similar whereas the distribution of orders in Prior set is different.
   * According to the plot of 'Total Orders VS Day of Week', we can see most of people buy groceries on weekends (0- Saturday, 1- Sunday)
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Total%20Orders%20per%20Day%20of%20Week.png)
   * From 'Orders VS Days since prior order' graph, we can know customers order once in a week which is supported by peaks at 7,14,21 and 30.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Orders%20VS%20Days%20since%20prior%20order.png)
   * Based on the heatmap between 'Day of Week' and 'Hour of Day,' we can say that majority of the orders are made during the day time, also Saturday afternoons and Sunday mornings are prime time for orders.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Frequency%20of%20Day%20of%20Week%20VS%20Hour%20of%20Day.png)
* products: This file contains the list of total 49688 products and their aisle as well as department. The number of products in different aisles and different departments are different.
* order_products_prior: This dataset provides information about which products were ordered and in which order they were added in the cart. It also shows us if the product was reordered or not.
   *  This table has total 3214874 orders and 49677 products were ordered.
   *  From 'Frequency of Items in Cart' plot, we can conclude most of people buy 1-17 items in an order and there were a maximum of 145 items in an order. 
   *  The percentage of reorder items in prior set is 58.97%.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Frequency%20of%20Items%20in%20Cart%20in%20Prior%20set.png)
* order_products_train: This file provides information about which products were ordered and in which order they were added in the cart.Also, it shows whether the products was reordered or not.
   *  There are total 131209 orders through which total 39123 products were ordered.
   *  From 'Frequency of Items in Cart in Train set' plot, we known that most of people buy 1-17 items in an order and there were a maximum of 145 items in an order.
   *  The percentage of reorder items in train set is 59.86%.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Frequency%20of%20Items%20in%20Cart%20in%20Train%20set.png)

## Exploratory Data Analysis
For EDA, I combined all of the separate data files into one single dataframe.
* This plot shows most popular aisles based on total orders and reorders.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Popular%20Aisles.png)

* From below plots, the reorder ratio of day-to-day food items is high whereas the other products such as vitamins, food storage, beauty etc. reorder ratio is low. It is clear that we buy only groceries regularly and do not buy other products in every order.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Aisle_High_Reorder.png)
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Aisle_Low_Reorder.png)

* The following plot shows popular departments. The website or App layout should be in a way that popular departments are very near to each other.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Popular%20Departments.png)

* Here is the most popular products. As we can see there are many organic products in the Top 20 popular products.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Most%20Popular%20Products.png)

* As we can see in below charts, there are less number of organic products but their mean reorder ratio is higher than inorganic product. It tells us that we should have more organic products in Instacart website and App.

![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Total%20Organic%20%26%20Inorganic%20Products.png)
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Mean%20Reorder%20Ratio%20of%20Organic%20%26%20Inorganic%20Products.png)

* According to add-to-cart-order and mean reorder percentage, we can see the lower the add-to-cart-order higher the reorder ratio. This makes sense as we mostly buy things at first that are required on day-to-day basis.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Add%20to%20Cart%20Order%20VS%20Reorder%20Ratio%20.png)
<imgsrc="https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Add%20to%20Cart%20Order%20VS%20Reorder%20Ratio%20.png"width='100px'> 

* In the plot of reorder percentage and number of product purchase, we can see a ceiling effect. Many people try different product once and they do not reorder agian. Also, there are users buy certain products regularly.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Reorder%20Percentage%20VS%20Total%20Orders.png)

* From below table, we can see that the total unique users of products having highest reorder ratio are only few (1-15 only). This means that these users like these products and would buy regularly.

![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Reorder_df.png)

* As the plot of cumulative total users per products VS products, we can see that 85% of the users buy only 10000 products out of 49688 products. If we are interested in shelf space optimization, we should have only these 10000 products. Here, I assume that the profit from remaining 39688 products are not significant high. If we had prices of these products, we could have considered the products having high revenue, high reorder percentage and high total product sale.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Cumsum_products.png)

## Customer Segmentation
Customer Segmentation is a way to divide customers into different groups based on common characteristics so the company can market to each group effectively and appropriately. Since there are thousands of products and also thousands of customers, I utilized aisles which represent categories of products.
I performed Principal Component Analysis to reduce dimensions as KMeans does not product good results on higher dimensions. By using 10 principal components, I carried out KMeans clustering, and chose optimal number of clusters as 5 based on Elbow method shown below.
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Elbow%20Method%20for%20Optimal%20k.png)

Here is the clustering:

![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/Cluster.png)

The clustering results into 5 neat clusters and after checking most frequent products in them, we can conclude following:
* Cluster 1 results into 37926 consumers who have a very strong preference for fruits followed by fresh vegetables.
* Cluster 2 results into 5417 consumers having a very strong preference for water seltzer sparkling water.
* Cluster 3 results into 99117 consumers who orders products from many aisles. Their mean order are lower than other clusters which tells us either they are not frequent users of Instacart or they are new users and do not have many orders yet.
* Cluster 4 results into 55801 consumers who mostly bought fresh vegetables followed by fresh fruits.
* Cluster 5 results into 7948 consumers buy packaged produce and fresh fruits mostly.

## Market Basket Analysis
Market basket analysis scrutinizes the products customers tend to buy together, and uses the information to decide which products should be cross-sold or promoted together. The term arises from the shopping carts supermarket shoppers fill up during a shopping trip.

Association Rule Mining is used when we want to find an association between different objects in a set, find frequent patterns in a transaction database, relational databases or any other information repository.

The most common approach to find these patterns is Market Basket Analysis, which is a key technique used by large retailers like Amazon, Flipkart, etc to analyze customer buying habits by finding associations between the different items that customers place in their “shopping baskets”. The discovery of these associations can help retailers develop marketing strategies by gaining insight into which items are frequently purchased together by customers. The strategies may include:

* Changing the store layout according to trends
* Customers behavior analysis
* Catalog Design
* Cross marketing on online stores
* Customized emails with add-on sales, etc.

### Matrices
I utilized apriori algorithm from Mlxtend python library and found out associations from top 100 most frequent products which resulted in 28 product pairs (total 56 rules) that have lift highr than 1, which means that there is a positive correlation within the itemset, i.e., products in the itemset, A, and B, are more likely to be bought together.
The top 10 product pairs having highest lift are shown below:

| ProductA | ProductB | Lift |
| ----- | ----- | ----- |
| Limes | Large Lemon | 3.01 |
| Organic Strawberries | Organic Raspberries | 2.21 |
| Organic Avocado | Large Lemon | 2.13 |
| Organic Strawberries | Organic Blueberries | 2.12 |
| Organic Raspberries | Organic Hass Avocado | 2.08 |
| Organic Fuji Apple | Banana | 1.88 |
| Bag of Organic Bananas | Organic Raspberries | 1.84 |
| Bag of Organic Bananas | Organic Hass Avocado | 1.82 |
| Honeycrisp Apple | Banana | 1.77 |
| Organic Avocado | Organic Baby Spinach | 1.70 |

## Machine Learning Model to Predict Product Reorders

In order to build a model, I need to extract features from previous order to understand user's purchase pattern and how popular the particular product is. I extract following features from the user's transactional data.

##### Product Level Features:
    1.Product's average add-to-cart-order
    2.Total times the product was ordered
    3.Total times the product was reordered
    4.Reorder percentage of a product
    5.Total unique users of a product
    6.Organic or Inorganic
    7.Percentage of users that buy the product second time
    
##### Aisle Features:
    8.Reorder percentage. Total orders and reorders of a product aisle
    9.Mean and std of aisle add_to_cart_order
    10.Aisle unique users
    11.Binary encoding of aisle feature
    
##### Department Features:
    12.Reorder percentage. Total orders and reorders of a product department
    13.Mean and std of department add-to-cart-order
    14.Department unique users
    15.Binary encoding of department feature

##### User Level Features:
    16.User's average and std day-of-week of order
    17.User's average and std hour-of-day of order
    18.User's average and std days-since-prior-order
    19.Total orders by a user
    20.Total products user has bought
    21.Total unique products user has bought
    22.User's total reordered products
    23.User's overall reorder percentage
    24.Average order size of a user
    25.User's mean of reordered items of all orders
    26.Percentage of reordered items in user's last three orders
    27.Total orders in user's last three orders
    
##### User Product Level Features:
    28.User's avg add-to-cart-order for a product
    29.User's avg days_since_prior_order for a product
    30.User's product total orders, reorders and reorders percentage
    31.User's order number when the product was bought last
    32.User's product purchase history of last three orders

### ML Model - XGBoost
Using the extracted features, I prepared a dataframe which shows all the products user has bought previously, user level features, product level features, asile and department level features, user-product level features and the information of current order such as order's day-of-week, hour-of-day, etc. The Traget would be 'reordered' which shows how many of the previously purchased items, user ordered this time.
I chose to use XGBoost as it handles large data, can be parallelized and gives feature importance. Since, we can hack the F1 score by changing the threshold, I relied on AUC Score for model evaluation. The performance of XGBoost Model is shown below using Confusion Matrix, ROC curve and classification report. The feature important plot from XGBoost model is shown to understand important features which help predict product's reorder. The performance of XGBoost performs great in terms of ROC-AUC.

#### XGBoost Model's Performance and Feature Importance:
<div align=center><img width='150' height='150 src = 'https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/XGBoost%20Report.png'</div>
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/XGBoost%20Performance.png)
![image](https://github.com/Chloeinthecloud/Instacart-Market-Basket-Analysis/blob/main/Plots/XGBoost%20Feature%20Importance%20Plot.png)

