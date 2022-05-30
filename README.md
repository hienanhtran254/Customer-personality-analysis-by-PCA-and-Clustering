# Customer personality analysis
Customer Personality Analysis is a detailed analysis of a company’s ideal customers. It helps a business to better understand its customers and makes it easier for them to modify products according to the specific needs, behaviors and concerns of different types of customers.

## 1. Background: 
This report aims to explore the dataset from customer-personality.csv to help a company understand their customers' behaviour.

## 2. Methodologies: 
For understanding customer personality and delivering a proper marketing strategy, we would choose dimension reduction method. It helps remove multicollinearity which improves the interpretation of the parameters of the machine learning model. To complete the final customer profiling, we applied both supervised and unsupervised learning.

## 3. Results of finding
### a. Supervised learning

![image](https://user-images.githubusercontent.com/92025453/166337013-c94bf782-fb23-43aa-acd1-a9f4c15bc423.png)
[Figure 1. Variable importance]

As making profit is the key of a business, we decided to use the variable of Total_Expenses as an independent variable. By fitting decision tree regressor and random forest regressor models with optimised 20 leaves, which produce low RMSE values for the test set, we decided to choose the random forest model and variables importance plot to determine which variables are important when considering a customer. Based on Figure 1, the 3 most important variables are Income, Total_purchase, and Total_childs. 

### b. Unsupervised learning
For unsupervised learning, we run 2 methods which are PCA and Factor Analysis (FA). 

![image](https://user-images.githubusercontent.com/92025453/166337089-5a001b14-59a5-4a19-903d-6e43ab376803.png)
Figure 2. Cumulative explained ratio (PCA)	

![image](https://user-images.githubusercontent.com/92025453/166337141-c014748f-821b-4b80-a55a-5c7d2359a4c1.png)
Figure 3. PCA scree plot

![image](https://user-images.githubusercontent.com/92025453/166337200-67372c33-8923-427d-8eaa-c108fba7a186.png)
Figure 4. Cumulative explained ratio (FA)	

![image](https://user-images.githubusercontent.com/92025453/166337212-14cf0c8d-7287-4a66-ad08-854bd9c0cae2.png)
Figure 5. FA scree plot

After considering cumulative explained ratio plot (Fig 2 and 4) and cree plot (Fig 3 and 5) with elbow rules of both methods, we would choose to analyse 3 components, which explained more than 50% of our variance. It seems the PCA method gives us higher cumulative variance compared to FA (57% and 54% respectively). 

According to Fig 6, correlation matrix of PCA loading factors show some patterns of loadings value at each component; they are not too obvious. This is because the goal of PCA is to extract maximum variance from a dataset with a few orthogonal components, in order to provide only an empirical summary of the dataset. Therefore we would choose Factor Analysis, which loadings can provide a clearer underlying pattern for each factor.

![image](https://user-images.githubusercontent.com/92025453/166337442-cbac5872-0286-42f9-9c98-ab48fe3ac957.png)
Figure 6. Heatmap of correlation matrix for loading factors

After saving the loading value into each variable, we would then group them to see the similarity between each factor. As a rule of thumb, the greater the loading, the more the variable is a pure measure of the factor. Moreover, Comrey and Lee (1992) suggest that loadings of >55% (30% overlapping variance) indicate good. Therefore, we would choose 55% as our threshold to look in detail at loading factors in factor analysis, shown as follow:

- Factor 1: Purchasing power (Income, MntWines, MntFruits, MntMeatProducts, MntFishProducts, MntSweetProducts, NumWebPurchases, NumCatalogPurchases, NumStorePurchases,, Total_Purchases) This factor seems to suggest purchasing power of a customer for the last 2 years.

- Factor 2: Children are important (Teenhome, Total_Childs, Family_members) This factor seems to be correlated with the number of children in the family.

- Factor 3: Deals shopper (NumDealsPurchases, NumWebVisitsMonth) This factor belongs to customers who love web browsing and bargain purchase.

After using Factor Analysis as a denoising step, we would do the Hierarchical and K-means clustering methods to have a better look at customers segment. For Hierarchical clustering, we have tried 3 methods (ward, complete and average), but then choose the `ward` method as it gives a better look at the branch (Fig 7). Additionally, we also use the K-means method to label our customers. With plotting the number of clusters vs inertia_K, it looks like the best number of clusters varies from 3 to 5 (Fig 8).

![image](https://user-images.githubusercontent.com/92025453/166338798-6b280456-e6ff-4e80-8573-ae62643eb1ba.png)
Figure 7. Hierarchical clustering based on ‘ward’ method

![image](https://user-images.githubusercontent.com/92025453/166337860-98f00f08-e2c7-4df3-9c1a-21a91de97366.png)
Figure 8. K-means clustering 			

![image](https://user-images.githubusercontent.com/92025453/166337886-471d3910-398f-4ab5-ab84-ef9b3914e6ad.png)
Figure 9. 3D plot of Clusters and 3 Factors

After considering the snake plot of different numbers of clusters, we then choose 3 clusters, which show no overlapping characteristic between clusters. Figure 6 describes the final decision of choosing 3 components based on the Factor analysis method and 3 clusters based on the K-means method in 3D graph. 

## 4. Customer profiling
Overall, details for each cluster can be visualised in the plots below:
(Note: the plots in part 4, except for the snake plot, are interactive. Please kindly run the code to open them.)

![image](https://user-images.githubusercontent.com/92025453/166338673-9ca29934-db1f-4e52-8832-3954dac8c5ff.png)
Figure 10. Snake plot of 3 clusters

![image](https://user-images.githubusercontent.com/92025453/166337970-bb2ee80c-39a8-4d13-abb5-d86a26ef4383.png)
Figure 11. Number of children at each cluster

![image](https://user-images.githubusercontent.com/92025453/166337979-3b431972-5f9f-4e93-a717-1ecf320e6ba7.png)
Figure 12. Total expense vs Income	Figure 13. Number of web monthly visit
 
![image](https://user-images.githubusercontent.com/92025453/166337999-d13d67eb-9283-43f2-9355-abb7c0caccc5.png)
Figure 13. Number of web monthly visit

![image](https://user-images.githubusercontent.com/92025453/166338035-17165273-7594-46f8-a642-a16b0c49e65c.png)
Figure 14. Number of purchase and amount spend on different products at each cluster

![image](https://user-images.githubusercontent.com/92025453/166338060-82aad265-57f8-4994-ab5a-3a2b0c3de352.png)
Figure 15. Number of purchase on different channels at each cluster

Summary personality of each clusters:
- Cluster 0 (1st segment):
  + Low income
  + Have 1 child, mostly kid
  + Regularly visit web
  + Average age around 43 years old
  + Mostly purchase at physical channels 
  + Lowest amount of spending

- Cluster 1 (2nd segment):
  + Middle income
  + Have lots of children, mostly teenagers
  + Sometimes visit website
  + Average age around 53 years old
  + Mostly are couples
  + Mostly purchase at physical channels, and sometimes are web
  + Loves deals purchases
  + Fan of wines, and some time spend money for meat

- Cluster 2 (3rd segment)
  + High income
  + Do not have kid
  + Rarely visit website
  + Average age around 57 years old
  + Highest amount of expense and number of purchase
  + Normally purchase at stores, frequently via web and catalogue, but hardly ever buy deals.
  + Wine and meat lovers; fish might be an alternative meal for meat; and occasionally bought sweet, fruits and gold.


## 5. Proposed marketing strategy
Every customer segment, according to the results of the profiling, has a strong online shopping behaviour. As a result, we advise the company to focus on their online strategy by offering sales and discounts. They will be able to fully track customer behaviour as a result of this, allowing them to tailor product suggestions and promotions to different groups of customers in the future. Furthermore, because the products are mainly grocery-related, we could launch a service such as a subscription model and home delivery for the convenience of the customers. Furthermore, the company would provide a guarantee on the quality of premium products as well as a return policy in order to attract high-income shoppers to digital platforms. 

#### REFERENCES
Comrey, A. L., & Lee, H. B. (1992). A first course in factor analysis (2nd ed.). Lawrence Erlbaum Associates, Inc.




