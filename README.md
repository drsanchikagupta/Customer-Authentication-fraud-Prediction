# Customer-Authentication-fraud-Prediction

1.	Data
The data has 5 columns: 
•	user A string indicating the username of the person authenticating.
•	application A string value with the name of the application being accessed.
•	device_type A string value with a description of the type of device used for a second
•	 time An integer value giving the time of day that the auth was made (seconds after midnight)
•	fraud 0/1 indicator of whether the authentication was fraudulent. 

I have loaded the data in  a df. The shape and info of the df is as follows:
df.shape

		(1014, 5)


df.info()
	<class 'pandas.core.frame.DataFrame'>
	RangeIndex: 1014 entries, 0 to 1013
	Data columns (total 5 columns):
	user           1014 non-null object
	application    1014 non-null object
	device_type    917 non-null object
	time           868 non-null float64
	fraud          1014 non-null int64
	dtypes: float64(1), int64(1), object(3)
	memory usage: 39.7+ KB

2.	Data Cleaning and Exploratory data analysis:
•	Find out the null values in the dataframe
•	Created a new column ‘device_type_new’ where null values are marked as ‘undefined’
•	Replaced the null values in time field with 0.
•	Found out the dataset has a class imbalance problem with 11.31 % of transactions being fraud.
•	The time field in the dataset is converted into morning, day, evening and night for idea of access information.



3.	Predictive Modeling: Steps taken for Predictive Modeling

•	Encoding: Convert categorical data: user, application and device_type into numeric values to be able to use in our model. Used one hot encoding to achieve the same.
•	Scaling: Used standard scaler to scale the time column to fit the range between (-1,1)
•	Feature Selection and Data split: In this process, we defined the independent (X) and the dependent variables (Y). Using the defined variables, we split the data into a training set and testing set which is further used for modeling and evaluating. We used the ‘train_test_split’ algorithm in python.
•	Modeling: Used Decision Tree, KNN and random Forest to model the data. 
•	Evaluation: Used Accuracy and f1 score for evaluation. Since it is a class imbalance problem, F1 score is a better metric for evaluation because it takes into account FP’s and FN’s.
•	Correlation: Found out the correlation of the predictors with the target variable ‘fraud’. Certain predictors have low correlation. Removed them from the data.
•	Again fitted the data using the above models and got better accuracy and F1 score.

Summary: Out of the 3 models above -- Decision tree, KNN and Random Forest tree we get the best results using the KNN model. The data above has a class imbalance problem. There are less number of fraudulent transactions. Given more time some measures can be taken to solve that to get better evaluation results for F1 score.

4.	Devices and Applications: Is the distribution of device_type dependent on the application being accessed, given the identity of the user performing the action? 

Grouped by device type and application to see the dependency and check the count. Found out the below information:

application    device_type
application_1  android        416
               iphone          55
               yubikey         67
application_2  android        234
               iphone         110
               yubikey         35
dtype: int64


As we can see from the above data device type android and yubikey are more in in count with application 1 as compared to application 2 and device type iphone is more in count with application 2. This doesnot mean that any particular device is dependent on any application. The data is distributed.
