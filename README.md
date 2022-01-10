# Phase-3-project

## Outline of this repo
Contained in this repo we have 3 files I have
1. phase3_final - this is the jupyter notebook with the whole analysis of the problem I was adressing 
2. Mod3_finalproject_PPP1 - this is a non-technical presentation of the problem I was adressing
3. syriatel_churn.csv - this is the data we were using for this project 

## phase3_final
I sarted of by outlining the problem and our goal for this project

I then did some EDA to futher understand the data. 
1. there was not much cleaning to be done
2. I dropped a few columns that would prove not to be important 
3. I onhotencoded some categorical values
4. I made a few graphs to visualise the data 

I broke the dataframe into training and testing data. I added a classweight to address the imbalance of the data.

I ran various models on the data:
1. Logistic regression 
2. decision tree
3. Random forest classifier
4. K Nearest neighbours
5. XGBoost
We evaluated the models based on the PR AUC metric. We decided to choose this metric as after reading we found that it works best for models where the 1 is more important than the o and where there is a class weight imbalance (when the 1 is more important than the 0)

Since we foudn that XGBoost model has the highest PR AUC we decided to optimise on this. 
We preformed a grid search.
We looked at the feature importance graph. 

