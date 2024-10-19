# MLOps-with-AWS
Automate end-to-end ML workflow for all the steps including data extraction, preprocessing, training, evaluation, data/model drift and deploying model in production with AWS Sagemaker Pipeline

Amazon SageMaker Pipelines is a purpose-built, easy-to-use continuous integration and continuous delivery (CI/CD) service for machine learning (ML). In this example, Sagemaker pipeline is used 
to preprocess Abalone data, train and evaluate an Xgboost model, record baselines for data quality and model quality and deploy the model in production.  

<img src="images/MLOps2_Muntasir Hossain.png?raw=true"/>

## Execution
The pipeline.py file is the main execution file. It can be used as is in the Sagemaker notebook instance or with a little modification in Sagemaker Studio. 
The preprocess.py and evaluation.py are files for preprocessing the training data and performing the model evaluation. The lambda_getapproved_model.py is 
the lambda function to get the latest approved model package and iam_helper.py is the helper function for the lambda_getapproved_model.py for the required execution role. 

## CI/CD with Sagemaker Pipeline
The image below shows a snapshot of the CI/CD pipeline in Sagemaker Studio.

<img src="images/Sageaker Pipeline4.png?raw=true"/>

## Deploying Model for Realtime Inference
A REST API was created by using Amazon API Gateway to demonstrate an external-facing, single point of entry for the Sagemaker model endpoint. A lambda function was employed to establish the communication  between the API gateway and the model endpoint. The API was tested with Postman (an HTTP client) for real-time inference. 

<img src="images/RealtimeInference-Postman.png?raw=true"/>

## Data Drift Check
Data drift was also monitored against the baseline training data quality with a batch inference monitor. The inference data was intentionally altered to contain some missing 
values for some features and change of data type (i.e. fractional to integers). Data drift was accurately demonstrated as shown below. 

<img src="images/data drift.png?raw=true"/>

