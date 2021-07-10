# HousePricingPredictions

Housing Price Predictions in Ames, IA
Team: Vijitha Samarasinghe, Lawrence Guloy, Clayton Grace

Purpose/Scope:

It is widely known that there are multiple variables that impact the price of a house. This project seeks to determine which variables have the highest influence on the price of a house. This project utalizes the Ames Housing dataset, which contains 79 explanatory variables describing many aspects of residential homes in Ames, IA. The purpose of this project is to analyze the Ames Housing dataset using machine learning in order to accurately predict the price of homes.

Methodology:

The first step for this project was to clean the data. The original dataset contains 81 columns. Both numeric and non numeric vlaues were found in the dataframe. Identified the requirement of data conversion to numeric values to perform the Machine learning model. A purely catergorical variables that were in the string format, converted to numerical values using pandas method called pd.get_dummies().   An ordinal variable is similar to a categorical variable found as well.  (The difference between the two is that there is a clear ordering of the categories.)  These ordinal variables were assigned to rank based values using pandas.DataFrame.replace method. sklearn ordinalencoder is another way to encode the ordinal variables. However, it was less efficient to these types of datasets.  Analysed the null values and either drop them or converted to zero, based on the attribute of the column. 
Cleaned test data and trained data files and transform to csv files consist all numeric values. Extracted data loaded to Amazon Web Services' (AWS) Simple Storage Service (S3) bucket to use for machine learning model and the wed development purposes. 

Once the data was cleaned, feature importance was determined for the varriables. With 81 different vairables, the model would run the risk of over-fitting if all 81 variables were used. To determine feature importance the dataset was first transformed to use dummy variables throughout in order to prepare the data for catagorization. A random forest categorical analysis was used to establish the feature importance scores of the data variables. From this model 10 variables with the highest feature importance were used for orice predictions.

A Random Forest Regression analysis was used to perform the price prediction model because the data set contains both qualitative and quantitative variables. Random Forest does not require scaling the data, which was also a factor in its use. The first step in the model was to import the cleaned and transformed training dataset. The training used an 80/20 split where 80% of the data was used to train the model and 20% was reserved to test the effectiveness of the model. The model uses the 10 variables determined by the feature importance analysis. The training score of the model is 97% and the test score is 85%. After the model was trained it was finalized by fitting to 100% of the data and then saved. The saved model was subsequently used on a final dataset with no price information. The final dataset was cleaned and transformed in precisely the same manner as the train-test dataset. The model was run on the dataset and a list of prices was projected.

Top ten feature importance data were selected from the cleaned dataframe and uploaded to AWS posgres database. Data visualization is performed using Tableau and dashboard can be found: https://public.tableau.com/views/HousePricing_Dashboard1/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link 

A web application was created so that users can input house information and run the data through the model to predict a house price. The application requires the same data inputs from the feature importance varriables. As a data collection process, the user imput are stored in separate table of posgres database that has mentioned earlier. The application was deployed using heroku and can be found at: https://lghousepredictions.herokuapp.com/

This project was derived from a Kaggle competition: https://www.kaggle.com/c/house-prices-advanced-regression-techniques/overview


