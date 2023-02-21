# Predict-US-Recessions

The objective of this project is to create models that can help predict a US recession using only market data, primarily the US Treasury yield curve and the SP500 index. The first model will try to predict a recession for the month of the data, and the remaining ones will try to predict a recession in 3, 6, and 12 months.

The main challenge I faced while building the models is the imbalance between classes, which at the beginning led to models that were highly accurate but failed to predict a minority class outcome (recession). After a lot of trial and error, I found the ADASYN algorithm from the imblearn library, that creates synthetic samples of the minority class in order to train the model with a balanced dataset. 

The chosen algorithm for this task is the GradientBoostingClassifier, which resulted as the best performing one. To add some randomness to the training process and reduce overfitting, I setted a subsample value of 0.4 and a minimum sample leaf of 8.

In order to choose the features, I used the pairplot function from seaborn and a correlation matrix. Then, I created the X matrix with the most correlated features. To choose the final features to fit the model I used a Sequential Forward Floating Selector with cross validation, and the F1 score as the defining metric. All the models were fitted using the best performing combination of the features, and then evaluated on a testing, separate dataset. To further evaluate the performance of the models on the testing dataset, I used the classification report function from the imblearn library.

At the end, I fit the models again using the whole dataset.

Overall, I'm pretty satisfied with the results, but I know there's still a lot of room for improvement. It's clear that the data selected as input has predictive value, and it also makes sense that the longer time frame predictions rely more on the shape of the yield curve than the shorter time frame ones. Additionally, the performance of the models decrease for the longer time frame predictions, implying that is harder to make predictions with more anticipation. 
