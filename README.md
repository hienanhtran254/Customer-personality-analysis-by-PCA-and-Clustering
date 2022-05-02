# Customer personality analysis
## 1. Background: 
This report aims to explore the dataset from customer-personality.csv to help a company understand their customers' behaviour.

## 2. Methodologies: 
For understanding customer personality and delivering a proper marketing strategy, we would choose dimension reduction method. It helps remove multicollinearity which improves the interpretation of the parameters of the machine learning model. To complete the final customer profiling, we applied both supervised and unsupervised learning.

## 3. Results of finding
### a. Supervised learning

[Figure 1. Variable importance](https://hienanhtran254.github.io/customer-personality-analysis-hienanhtran254/1.Importance.html)

(https://automating-gis-processes.github.io/exercise-5-HTenkanen/test_map.html)



As making profit is the key of a business, we decided to use the variable of Total_Expenses as an independent variable. By fitting decision tree regressor and random forest regressor models with optimised 20 leaves, which produce low RMSE values for the test set, we decided to choose the random forest model and variables importance plot to determine which variables are important when considering a customer. Based on Figure 1, the 3 most important variables are Income, Total_purchase, and Total_childs. 


