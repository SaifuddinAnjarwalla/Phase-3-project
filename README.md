# Phase-3-project

## Outline of this repo
Contained in this repo I have 3 files I have
1. phase3_final - this is the jupyter notebook with the whole analysis of the problem I was adressing 
2. Mod3_finalproject_PPP1 - this is a non-technical presentation of the problem I was adressing
3. syriatel_churn.csv - this is the data I used for this project 

## phase3_final
### The problem and our goal for this project:

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

![test](https://github.com/SaifuddinAnjarwalla/Phase-3-project/blob/main/phase3/datapicture.png)


1. 21 different variables 
2. Key Dependent variable: 
     ‘Churn’ – 1(customer has churned), 0(customer has not churned)
3. Independent variable examples: 
       International plan: true if the user has the international plan, otherwise false
       Total day minutes: total number of minutes the user has been in calls during the day
       Total eve calls: total number of calls the user has done during the evening
       Customer service calls: number of customer service calls the user has done


### To understand the data i then did some EDA to futher understand the data. 
there was not much cleaning to be done:
1. I dropped a few columns that would prove not to be important 
2. I onhotencoded some categorical values
3. I made a few graphs to visualise the data 
![churnvnonchurn](https://github.com/SaifuddinAnjarwalla/Phase-3-project/blob/main/phase3/churnvsnonchurn.png)

![churnbystate](https://github.com/SaifuddinAnjarwalla/Phase-3-project/blob/main/phase3/churnbystate.png)



### The model

I broke the dataframe into training and testing data. I added a classweight to address the imbalance of the data.

I ran various models on the data:
1. Logistic regression 
2. decision tree
3. Random forest classifier
4. K Nearest neighbours
5. XGBoost
I evaluated the models based on the PR AUC metric. I decided to choose this metric as after reading I found that it works best for models where the 1 is more important than the o and where there is a class weight imbalance (when the 1 is more important than the 0)

Since I foudn that XGBoost model has the highest PR AUC I decided to optimise on this. 
I preformed a grid search to find the optimal parameters. I found that our model had an PR AUC score of 0.84

Below is the confusion matrix and classification report of our model.
![matrix](https://github.com/SaifuddinAnjarwalla/Phase-3-project/blob/main/phase3/matrix.png)

Positive = churns, negative = doesn't churn

36 - a customer churns and the model predict that it churns - True positive

2.8e+02 - a customer doesnt churn and the model predict that it doesnt churns - true negative 

4 - a customer churns and the model predicrt that it doesnt churn - flase positive

12 - a customer doenst churn and the model predict that it churn - false negative

![classification](https://github.com/SaifuddinAnjarwalla/Phase-3-project/blob/main/phase3/classificationreport.png)


Precision - ability of a classifier not to label an instance positive that is actually negative and vice versa (Precision = TP/(TP + FP))

Recall - ability of a classifier to find all positive instances. For each class it is defined as the ratio of true positives to the sum of true positives and false negatives.

F1 score - weighted harmonic mean of precision and recall such that the best score is 1.0 and the worst is 0.0.

macro avg - function to compute f1 for each label, and returns the average without considering the proportion for each label in the dataset. 

weighted avg - says the function to compute f1 for each label, and returns the average considering the proportion for each label in the dataset



### How can the telco identify churn 

I created a feature importance graph from our model.
![featureimp2](https://github.com/SaifuddinAnjarwalla/Phase-3-project/blob/main/phase3/featureimp.png)

1. High numbers of Customer service calls are associated with churn. 
![csccalls](https://github.com/SaifuddinAnjarwalla/Phase-3-project/blob/main/phase3/csc_calls.png)

0 service calls = 13% churn 

4 service calls = 46% churn 

8 and 9 service calls = 100% churn 

The larger the number of service calls a customer has to make the higher the chance of the customer curning.

2. Customers with an International Plan seem to churn.
![internationalplan](https://github.com/SaifuddinAnjarwalla/Phase-3-project/blob/main/phase3/international_plan.png)

No international plan = 11% churn 

Yes international plan = 42% churn 

Customers enrolled into an international plan seem to curn more than customers who are not.



### Conclusion

After analyzing the data I created a model to predict churn.

I tuned our model to get a PR AUC of 0.84.

The Telco can use this model in the future to predict which of its customer will churn.

I found a number of features that were important to look at to identify churn. To name a few these were:
1. Total time spent on the phone (day, night and evening minutes)
2. Whether the customer has an International plan
3. How many customer service calls a customer makes

