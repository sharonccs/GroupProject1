# GroupProject1

1.	Objectives

This project built machine learning models that predicted the selling price of a used vehicle given a set of vehicle features such as year, gas type, transmission type and location. The predictive model can help consumers to evaluate whether an asking price of a used vehicle is reasonable and therefore make the right decision. 

The project used a dataset on Kaggle that was web-scraped from Craigslist. We built, evaluated and compared four models: linear regression, lasso regression, linear support vector machine and Extra Tree Regressor. Our goal was to determine one model with the highest predictive performance. 


2.	Data Preparation

The raw data has 25 columns with a maximum of 539,759 unique row values. The biggest challenge we face is the many missing values for important features such as “manufacturers”, “transmission”, “fuel”, “cylinder” and “odometer”. These can, however, often be found in the text embedded in the “Description” and “Model” features. We have run a few scripts to locate and extract the needed information from the “Description” and “Model” features, cross-checked and then used them to fill in the missing values.

We dropped observations (rows) of any remaining missing values or any outliers of variables such as “year”, “odometer” and “prices”. We also dropped features (columns) that are either not useful for the models, or contain too many missing values.  These dropped columns are “ID”, “county”, “vin”, “url”, “paint_color”, “image_url”, “region_url” and “size”. Other data cleaning includes corrections to misspelling etc. 

Our final cleaned dataset has 250,573 records and 14 features (“region”, “year”, “manufacturer”, “condition”, “cylinders”, “fuel”, “odometer”, “title_status”, “transmission”, “drive”, “type”, “state”, “longitude” and “latitude”).


3.	Model Design

Our model design consisted of the following four major steps. 

First, we explored by visualizing the data. We found that a used vehicle on average, sells for higher prices if it has less mileage, is newer, in a better condition, with 3/8/10 cylinders, using diesel or electric fuel, with CVT transmission, with AWD or 4WD, or being sold in less-populated states. 

Second, we pre-processed and transformed data for our pipelines. This included one-hot encoding of all categorical variables and scaling of all continuous and discrete numerical variables. 

Third, we chose four models to train our dataset. They were:

●	Linear regression model: this served as our baseline case.
●	Lasso regression model: this is a linear regression model that estimates sparse coefficients, effectively reducing the number of features used in the model. 
●	Linear SVR model: this allowed us to model non-linear relationships.
●	ExtraTreeRegressor: this uses an ensemble approach instead of an individual-model approach. The ExtraTreeRegressor uses random subsampling, random node-splitting and aggregate averaging to improve predictive performance.

Fourth, for each model, we conducted three sets of sensitivity analysis in terms of the features included in the model. For example, some features, such as odometer and year, are negatively correlated, in which case we used Principal Component Analysis (PCA) as an alternative. 


4.	Model Evaluation

We used R2 scores to evaluate the trained models on the test dataset. The ExtraTreeRegressor had by far the best performance. It yielded an R2 score of 90%-92%, compared to 48%-78% produced by the other three individual-based models. This was not surprising, as the ExtraTreeRegressor uses an ensemble approach which typically improves model performance by reducing the variance of the model.

In addition, we found that location affects pricing, as the R2 score in our final chosen ExtraTreeRegressor model was slightly better when we included “region” features (92.3%) or a “region” PCA (92%) than that without the region features (90%).  


5.	Conclusions

Among the four machine learning models that we trained and evaluated, we found that the best model in predicting the selling price of a used vehicle is the ExtraTreeRegressor. The ensemble method outperforms the other three individual models by having the highest R2 score. Factors that influence a used-vehicle price include: millage, age, condition, cylinders, fuel type, transmission type and location
