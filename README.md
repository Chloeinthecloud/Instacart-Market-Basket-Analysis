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
