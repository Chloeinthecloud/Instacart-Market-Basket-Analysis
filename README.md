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
