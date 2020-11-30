# Vector-
Data Analytics on Video Games sales
 
### Components

##### XGBoost is an iterative approach. It trains the models in succession where each new model is trained to correct errors made by previous one. New errors are allowed but prevents the past errors. We then train the model using xg.train() function. Finally we use our model to predict the sales of the test dataset.The XGBoost model, proved to have an accuracy of 99.53% on test data. This algorthm has the best combination of prediction performance and processing time compared to otehr algorithms.

##### Since we have several independent variables, we would like to build a multiple linear regression model in order to compare the accuracy with the previously built XGBoost model. On training the model, we input test data points to model and found an accuracy of 99.99%. The multiple linear regression model involving all the variables had the testing score of 99.99%.  

##### The linear regression model built using the 3 principal components proved to have an accuracy of 94.94%.We used another approach where we found principal components using PCA and modelled a linear regression model. Using 3 principal components which explains a variation of 62.03% of the entire dataset, we trained the linear regression model which gave us a test accuracy of 94.9% and a training accuracy of 97.7%.


### Parameters Setting
We are training a model on a dataset and used for the prediction. Boosting takes an iterative approach to train the models in succession, with each new model being trained to correct the errors made by previous one.

We can define the parameters of our gradient boosting ensemble. We’ve set up some of the most important ones below to get us started.

   
   xgb param{
   
    'eta': 0.01, - Learning Rate can be in the range of (0.005,0.3)
    
    'max_depth': 5, - Maximum depth of the decision trees being trained . Can be in the range of (3,10)
    
    'subsample': 0.6,
    
    'colsample_bytree': 0.7, #range 0.5 to 0.9 
    
    'objective': 'reg:linear', - The loss function being used
    
    'eval_metric': 'rmse',  - The evaluation metric used is Root mean sqaured error.
    
    'silent': 1
    

 }
 
-> _num_boost_round_ corresponds to the number of boosting rounds or the tree built. Its optimal value depends highly on other parameters and must be retuned everytime a parameter is updated. Ideal in our case would be (>=500).

-> _early_stopping_rounds_ is used to avoid overfitting : It works by monitoring the performance of the model that is being trained on a separate test dataset and stopping the training procedure once the performance on the test dataset has not improved after a fixed number of training iterations.

-> _n_components_ used for PCA can have any number within the range (1-9) as it is upto us to choose the number of principal components we wish to use to train the model.The change here is reflected in the variable _explained_variance.
