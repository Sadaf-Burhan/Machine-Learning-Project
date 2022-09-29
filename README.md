# Machine-Learning-Project
PREDICTING GROCERY SALES FOR FAVORITA STORES IN ECUADOR
The goal of this project is to predict grocery store sales from an Ecuadorian grocery retailer, Favorita. The hypothesis is that grocery sales are impacted by time of year, oil prices, and holidays and that data can be modeled to predict sales volumes. As Ecuador is an oil-dependent country and economic health is correlated with oil price, daily oil prices will be considered during the analysis. Oil prices may impact the sales of groceries/goods and can be a key dimension in the model. Holidays/holiday seasons can also impact sales of groceries, especially food. Therefore, holidays will be included into the model as well. The business problem that this model addresses is forecasting product demand. If a product is overstocked beyond consumer demand, this can lead to excess costs and inefficiencies to the business by way of additional storage space and spoiled inventory. On the other hand, if a product is understocked and does not meet consumer demand, this can lead to dissatisfied customers and reduced revenue. An accurate model for grocery sales prediction can lead to increased profit, improved efficiencies, and higher customer satisfaction for the business.
Data Source: https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data The main dataset was separated into multiple csv files and required left merges. The main dataset included 2013-2017 data with target sales,oil prices, holiday information, transactions, store number, stores arranged in clusters, store types, cities, states, family of sale items and number of items on promotions. Another blind dataset (named as test) contained only 2 weeks of data (from 2017-08-16 to 2017-08-31), which had all the features except the sales column. This was available for sales forecast. Oil prices showed a positive auto-correlation, so missing values were back filled. The holiday dataset required some feature engineering after which 3 columns of holidays were added to the main dataset as National Holiday, Regional Holiday and Local holiday.Once data was cleaned and merged, data analysis and XGBoost Regressor model was implemented for prediction of sales.

XGBoost (eXtreme Gradient Boosting) is an optimized version of the gradient boosting framework of decision trees. In this model an iterative optimization algorithm is used to minimize the loss function. The loss function quantifies how far off prediction is from the actual result for a given data point. The better the predictions, the lower will be the output of the loss function. Therefore the main idea of this model is to minimize the loss function across all data points.
Prior to model design, data analysis was carried out. Upon expanding the trends, the major decrease in oil prices from 2014-Jan2015, highlighted the recession period. On the contrary sales and promotions had an increasing trend from July 2015 onwards. By 2016, the oil prices started stabilizing again. Therefore it was important to study the correlations of Sales, Oil prices and Promos. Upon checking the bimodal data distribution of oil prices, it was more suitable to select the time frame from 2016 onwards. The main idea was to avoid any biases in model training caused by the high prices of oil, pre-recession. Then categorical variables were analyzed and found that the type of the stores and products by family were the most promising features in terms of sales. Among holidays only National Holiday had a 10% impact on sales increase. After finalizing the features, a pipeline was designed to perform standard scalar transformations and one-hot encoding. Train/Test split was made using 80-20 ratio. For model evaluation, both built-in functions for cross validation and GridSearchcv of sklearn were used. The model achieved above 90% accuracy score for train and test. R2: 0.925, Y_predict Accuracy (RMSE): 6016.24 which lies in the std deviation intervals of the predictor variable. Learning curves also showed that XGBoost was a good predictive model. Feature importance plots were used to study the features that contributed most in the accurate prediction of XGBoost Regressor.
