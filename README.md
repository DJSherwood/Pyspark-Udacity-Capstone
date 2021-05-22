# Why Do Sparkify Users Churn? 

Full instructions for creating an EMR cluster are beyond the scope of this readme. 
Briefly setup is as follows: 

1. Login to Amazon Web Services ( https://aws.amazon.com ) and search for 'EMR Studio'
2. Select 'Clusters' on the left-hand side and then 'Create Cluster' ( blue button ) 
3. Follow instructions and configure as desired

At some point in the setup process, you will be prompted to specify which version of Spark should be installed. 
This project used Spark 3.0. 
The python library is Pyspark. 

The motivation behind this project was to determine which user-behaviors and service-interactions would predict user 'churn' -- that is, which users will quit the app. 

Although Sparkify is a fictional, music-streaming service, the dataset was created by Udacity to simulate the challenges that data scientists face every day. 
The dataset is composed of 26 million rows, making it almost impossible to model outside of a distributed framework like Spark. 

`Sparkify_Cluster.ipynb` will run on the full dataset but it will take some time. 
Consider adding additional nodes: I originally used 3 of the mxLarge size. 

# Summary of Results
Odds-Ratios computed from the data indicate that: 

* the number of advertisements
* the number of 'thumbs down' ratings
* the average number of hours spent in a single session

lead to more customer 'churn' while

* the number of hours as a free / paid user
* type of browser / gender 

lead to _less_ customer 'churn'. 

The final area-under-the-curve ( AUC ) for the training and testing sets was 0.75, which indicates that the model is under-fitting. 
Future work involves finding more features and training more powerful algorithms. 

# Acknowledgements
The data is available in Udacity's bucket `s3n://udacity-dsnd/sparkify/sparkify_event_data.json`