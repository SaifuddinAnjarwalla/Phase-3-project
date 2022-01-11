# Phase-3-project

## Outline of this repo
Contained in this repo we have 3 files I have
1. phase3_final - this is the jupyter notebook with the whole analysis of the problem I was adressing 
2. Mod3_finalproject_PPP1 - this is a non-technical presentation of the problem I was adressing
3. syriatel_churn.csv - this is the data we were using for this project 

## phase3_final
###I sarted of by outlining the problem and our goal for this project:

Our goal is to create a model to predic churn and alert the company on how to identify churn.

Customer churn is the loss of clients or customers. Predicting churn can help the Telecom company for many different reasons. 

### Our data
* state: the state the user lives in
* account length: the number of days the user has this account
* area code: the code of the area the user lives in
* phone number: the phone number of the user
* international plan: true if the user has the international plan, otherwise false
* voice mail plan: true if the user has the voice mail plan, otherwise false
* number vmail messages: the number of voice mail messages the user has sent
* total day minutes: total number of minutes the user has been in calls during the day
* total day calls: total number of calls the user has done during the day
* total day charge: total amount of money the user was charged by the Telecom company for calls during the day
* total eve minutes: total number of minutes the user has been in calls during the evening
* total eve calls: total number of calls the user has done during the evening
* total eve charge: total amount of money the user was charged by the Telecom company for calls during the evening
* total night minutes: total number of minutes the user has been in calls during the night
* total night calls: total number of calls the user has done during the night
* total night charge: total amount of money the user was charged by the Telecom company for calls during the night
* total intl minutes: total number of minutes the user has been in international calls
* total intl calls: total number of international calls the user has done
* total intl charge: total amount of money the user was charged by the Telecom company for international calls
* customer service calls: number of customer service calls the user has done
* churn: true if the user terminated the contract, otherwise false
![image](https://user-images.githubusercontent.com/59200380/148935235-c5ae7d95-8395-4fc2-8def-a8e49f11f5b9.png)




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

