# Predict-US-Recessions

The objective of this project is to create models that can help predict recession using only market data, primarily the US Treasury yield curve and the SP500 index.

The main challenge I faced while building the models is the imbalance between classes, which at the beginning led to models that were highly accurate but failed to predict a minority class outcome (recession). After a lot of trial and error, I found the ADASYN algorithm from the imblearn library, that creates synthetic samples of the minority class in order to train the model with a balanced dataset. 

The chosen algorithm for this task is the GradientBoostingClassifier, which resulted as the best performing one.

In order to choose the features, I used the pairplot function from seaborn and a correlation matrix. Then, I created the X matrix with the most correlated features. To choose the final features to train the model I used a Sequential Forward Floating Selector with cross validation, and the F1 score as the defining metric. All the models were fitted using the best performing combination of the features, and then evaluated on a testing, separate dataset.

At the end, I fit the models again using the whole dataset.
