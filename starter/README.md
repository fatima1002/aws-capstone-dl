# Object detection on Amazon Bin Images
This repo contains the the Capstone project soluton to Udacity AWS Machine Learning Engineer Nanodegree Program. The project consists of using a pre-trained CNN and applying transfer learning to predict the number of items in an image. The project was conducted in AWS sagemaker instance.

## Project Set Up and Installation
To set up a project please do the following:
1. Lauch and AWS Sagemaker Studio instance
2. All code is found in the following files: 
    1. `sagemaker_train.ipynb` : This contains the code that will train download and upload the dataset, train and evaluate all models.
    2. `train.py`: This contains the training code that will conduct hyperparameter tuning
    3. `train_debugprog.py` : This contains the code that trains the model using optimal hyperameters. Please note the `net()` and `net_dl()` contain the code that pertains to the benchmark vs more complictaed models respectively. The relevant one is uncommented when is use. 

## Dataset

### Overview
The dataset has been provided by Amazon[https://registry.opendata.aws/amazon-bin-imagery/]. A subset of this data has been downloaded using file_list.json

### Access
Download the data from a publicly available repo using wget and unzip data into the AWS filesystem (s3)

## Model Training

The final model chosen for this project is ResNet50. This proved to be the model that provided a high accuracy during experimentation. It is also a state of the art model used for image modelling. 

We also applied hyperparameter tuning, the following were tuned:
- learning rate (lr): Controls how much to change the model in response to the loss when the model weights are updated. If too high the weights change too much and we increase error , if too low the model will take a long time to converge.

- batch size : We want the highest batch size that will allow for fast training but also without impacting the loss too greatly.

- epochs: We would like the best model without overfitting the model.

Two models were trained known as:
1. Benchmark model : this model is the basic model 
2. DL model : this model applies a more complicated feed forward network for transfer learning. 

The models were also evaluated using a confusion matrix and calculating precion and recall for each class. Please view `finalreport.pdf` for commentary. 

For each model we viewed Debugger and Profiler outputs. Debugger commentary is also found in the `finalreport.pdf` , the profiler reports for both models are found here:
1. [Benchmark model](baselinemodelprofiler/ProfilerReport/profiler-output/profiler-report.html)
2. [DL model](dlmodelprofiler/ProfilerReport/profiler-output/profiler-report.html)

## Machine Learning Pipeline
1. Download and upload data to S3
2. Hyperparameter Tuning
3. Debugger and Profiler
4. Evaluation of the models
 
