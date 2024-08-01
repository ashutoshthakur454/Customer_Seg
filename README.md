# Customer Segmentation 


<div style="text-align: right;">
  <img src="https://github.com/user-attachments/assets/95cbc19d-40bf-43ae-beab-5f5adca5d862" alt="Image" style="width: 400px; height: auto;">
</div>


## Problem Statement:
 **Context** :
    Customer Personality Analysis is a detailed analysis of a company’s ideal customers. It helps a business to better understand its customers and makes it easier for them to modify products according to the specific needs, behaviors and concerns of different types of customers.

   Customer personality analysis helps a business to modify its product based on its target customers from different types of customer segments. For example, instead of spending money to market a new product to every customer in the company’s database, a company can analyze which customer segment is most likely to buy the product and then market the product only on that particular segment.
<br><br>
**Task:** Need to perform clustering to summarize customer segments.

## Data preprocessing & Feature Engineering

1) Missing values were imputed through median.
2) Created Age feature from customer's birth date.
3) Created Days_Since_Customer to demonstrate the number of days since the customer enrolled
4) Created Num_Kids & Fam_size for family size analysis.
5) Created Num_accepted which accounts for all the accepted offers by the customers from the previous 5 campaigns
6) MntTotal : Total amount spent by a customer in the last two years

## Exploratory Data Analysis
{Keeping response(i.e. if customer accepted the offer in the last campaign) as the target column : Reason behind this is to figure out why/what makes customers accept our last campaign offer}

1)  **Box-plot of all the features**
    ![image](https://github.com/user-attachments/assets/94f3f885-4cd9-4026-90cc-b2246bb760c9)
**We will not remove the outliers as Response column has imbalanced data distribution. We can loose information corresponding to the case when customer has accepted the offer in the last campaign**

2) **Relation Between Education, Income & Response**

  ![image](https://github.com/user-attachments/assets/ba726d97-8dff-4c20-b95e-cc834913b146)

   ![image](https://github.com/user-attachments/assets/377832fb-e696-4bcf-aa85-172a78689f69)

3) **Does Recency affect Responses?**
   (Recency is the Number of days since customer's last purchase)

   ![image](https://github.com/user-attachments/assets/bc239c2d-5070-4770-8d87-dcc4ad21dc5d)

4) **How have customers spent in the last two years?**
   
   ![image](https://github.com/user-attachments/assets/7cc52b27-0540-466d-92cd-30b712fa0bb2)

   ![image](https://github.com/user-attachments/assets/fc1cae75-74f6-4dd3-82b5-9a55ee348f64)


5) **Does Family Size affect purchases?**

   ![image](https://github.com/user-attachments/assets/4d13e2bb-3abe-4576-8b8a-fa255a91ab10)

   ![image](https://github.com/user-attachments/assets/7ceea1bb-ab9e-4dfd-86fc-8b049ca346e6)

6) Purchases made at stores/website/catalog/discount purchases

![image](https://github.com/user-attachments/assets/714b6eb4-7360-4286-9468-83cf6973ea96)

7) **Checking for patterns in purchases made through store, website and catalog**
   ![image](https://github.com/user-attachments/assets/0eeda750-4aba-4c1b-98ce-215ef209d3c0)

8) **Older people have more complaints?/ How have people with complaints reacted towards last campaign?**

   ![image](https://github.com/user-attachments/assets/2cc44d4b-239b-494d-b154-158d7ab27d98)

9) **Regular customers seem to be happy**

![image](https://github.com/user-attachments/assets/3f7671ae-4019-4009-8172-83eb56a211a5)

10) How do features correlate ?

    ![image](https://github.com/user-attachments/assets/df0ca8c5-80d8-4bfc-9ee1-3aa3b589f6d6)

**Correlation Coefficients for response:**<br>
![image](https://github.com/user-attachments/assets/6e9c47cb-5cd3-4f1e-aaf6-043646a2ae21)

# Conclusions after EDA:

## 1) Education and Income : 

We observed that customers with only basic education tend to have lower income levels. Interestingly, higher income customers show a higher probability of accepting offers. This suggests that marketing efforts might need to be tailored differently for varying income groups, possibly offering more appealing incentives to lower-income customers to increase their acceptance rates


### 2) Recency and Offer Acceptance:

Our data indicates that customers who have not made a purchase recently are less likely to accept new campaign offers. This highlights the need for continuous engagement strategies. To address this, we could implement re-engagement campaigns targeted at these customers to remind them of our products and services


### 3) Spending and Campaign Acceptance:

Our analysis shows that customers who have spent more in the past two years are more likely to accept new campaign offers. This suggests that high spenders value our products, and we should consider offering them personalized incentives or loyalty programs to maintain their engagement and encourage further spending


### 4) Family Size and Campaign Response:

Interestingly, smaller families are more responsive to campaign offers and tend to spend more. This insight can help us design family-size-specific campaigns. For larger families, we might need to offer bundled products or family-oriented discounts to increase their spending and campaign acceptance.


### 5) Purchase Channel and Campaign Acceptance:

Our data reveals that customers who make fewer purchases online or through catalogs are less likely to accept campaign offers. This indicates a need to enhance our online and catalog engagement strategies, perhaps by improving the user experience on these platforms or offering exclusive online deals to boost their interest and participation


### 6) Age, Complaints, and Campaign Participation

We found that older customers tend to lodge more complaints. However, this does not affect their participation in campaigns. This highlights an opportunity to improve our customer service for older demographics, ensuring their issues are addressed promptly while maintaining their engagement with our campaigns.


### 7) Historical Acceptance and Current Campaign Response

Customers who have historically accepted more offers are more likely to accept the current campaign. This suggests that our loyal customers are consistently engaged. We should leverage this by targeting these frequent acceptors with exclusive offers and early access to new products to maintain their loyalty and encourage continued participation

## Dimensionality Reduction

![image](https://github.com/user-attachments/assets/1e447c1a-a06c-4f34-abc3-2c8f70667c56)

We initially reduced the 22 features to 2 principal components using PCA to visualize the data.

<img src="https://github.com/user-attachments/assets/b00e028a-5067-47e5-a931-c97c72afc875" alt="image" width="400"/>

Upon visualizing the data in 2D, we observed that it was challenging to differentiate between the entries with response 0 and 1. So we proceeded to 3 n_components.

<img src="https://github.com/user-attachments/assets/c8c27a90-c14f-4138-b687-04bba7509d95" alt="image" width="700"/>

We performed clustering, with 3 components using K-means clustering . Here is the Elbow curve:

![image](https://github.com/user-attachments/assets/e96bdbc3-5de2-4655-94c5-36232012459d)

We visualized the clusters in a 3D plot using the first three principal components."

![newplot (6)](https://github.com/user-attachments/assets/17c1caef-c2c3-46af-baed-2de4e50ba05a)

The 3D visualization helped us understand the separation and distribution of the clusters better.

Realizing that 2 components only explained a small portion of the variance, we increased the number of components to 3, which improved the explained variance but was still not enough. Eventually, we increased it to 7 components, capturing 72% of the total variance

![image](https://github.com/user-attachments/assets/31e97b47-aead-47bf-9206-ce82315a75b9)

![image](https://github.com/user-attachments/assets/a67c52c0-7386-48e0-9baa-164bc22e7bf4)

## Visualising the clusters:

1) **Income V/s Clusters:**

![image](https://github.com/user-attachments/assets/208be2e3-12e8-4b45-a693-61419d1fe7a7)

2) **Age V/s Clusters:**

![image](https://github.com/user-attachments/assets/8182914a-8581-4344-b834-4e36bd6953c6)

3) **Money Spent V/s Clusters**

![image](https://github.com/user-attachments/assets/3d81c80c-6f59-4c82-9043-d7e5164deea1)

4) **Total Purchase Number V/s Clusters**

 ![image](https://github.com/user-attachments/assets/fba798c5-705a-4315-acb4-da2fd30a48ea)

5) **Family Size V/s Clusters**

![image](https://github.com/user-attachments/assets/bb8660ba-cc90-4f82-9f3a-d911689689c8)

6) **Number of Discounted Purchases V/s Clusters**

![image](https://github.com/user-attachments/assets/3f0ed098-2e68-470b-a18a-ef5d7e30b582)

7) **Previous Accepted Offers**

![image](https://github.com/user-attachments/assets/c40bf84f-6eb0-454c-b99d-3b0c9e6ff824)

8) **Number of days since customers enrolled**

![image](https://github.com/user-attachments/assets/8cc86078-d527-4b27-bed0-1c4a730acc0d)

# Summary Of clustering:

**Cluster 0 :**

*Comprises of 46% customers (Largest pool)<br>
*Least Income<br>
*Least money spent<br>
*Least Number of purchases<br>
*Large Family size<br>

**Cluster 0 is our largest customer segment, making up 46% of our customer base. These customers generally have the lowest income and spending, along with the least number of purchases. They also tend to have larger families. To better engage this segment, we should consider offering budget-friendly promotions and products that cater to larger families**

**Cluster 1:**

*Oldest Cluster<br>
*low income + low spending<br>
*Long time customer<br>
*Largest Family size<br>
*Highest number of purchases with discount<br>

**Cluster 1 consists of our oldest customers who have been with us for a long time. They have low income and spending but are very loyal and frequently use discounts. This cluster also has the largest family sizes. To retain their loyalty, we should continue providing targeted discounts and special offers, emphasizing our appreciation for their long-term support**

**Cluster 2:**

*High income<br>
*High number of purchases<br>
*Low family size<br>
*Doesnt utilise discounts much<br>

**Cluster 2 includes customers with high income who make frequent purchases. They generally have smaller families and don't utilize discounts much. This indicates that they value quality and exclusivity over discounts. To engage this segment, we should focus on offering premium products and services, possibly through a loyalty program that provides exclusive benefits**

**Cluster 3:**

*Smallest pool (only 9%)<br>
*Highest Income and spending<br>
*Most purchases<br>
*Low family size<br>
*Regular customers<br>

**Cluster 3 is our smallest segment, comprising only 9% of our customer base, but they are our most valuable customers. They have the highest income and spending levels and make the most purchases. These customers are regular shoppers with small family sizes. To retain and reward these high-value customers, we should implement personalized marketing strategies and VIP programs that offer exclusive benefits and experiences.**
