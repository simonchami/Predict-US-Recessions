# Predict-US-Recessions

The goal of this project is to create models that can help predict a US recession using only market data, primarily the US Treasury yield curve and the SP500 index. The first model will try to predict a recession for the month of the data, and the remaining ones will try to predict a recession in 3, 6, and 12 months.

The main challenge I faced while building the models is the imbalance between classes, which at the beginning led to models that were highly accurate but failed to predict a minority class outcome (recession). After a lot of trial and error, I found the ADASYN algorithm from the imblearn library, that creates synthetic samples of the minority class in order to train the model with a balanced dataset. 

The chosen algorithm for this task is the XGBoostClassifier, which resulted as the best performing one. To evaluate and tune the model, I built some custom functions that make various splits on the data, transform the training data and score on the test data. I did this to be able to train using resampled data, but test on raw data.

At the end, I fit the models again using the whole dataset.

Overall, I'm pretty satisfied with the results, but I know there's still a lot of room for improvement. It's clear that the data selected as input has predictive value, and it also makes sense that the longer time frame predictions rely more on the shape of the yield curve than the shorter time frame ones. Additionally, the performance of the models decrease for the longer time frame predictions, implying that is harder to make predictions with more anticipation. 
