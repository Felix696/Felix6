# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
This dataset contains data about bankmarketting in a csv form. We seek to predict the value of the chosen column(y) which is if there will be a subscription or not.
The best performing model was the model done using the Azure AutoML run. It offers more precise data handling.

## Scikit-learn Pipeline
The pipeline uses a compute cluster with vm size of Standard_d2_v2. The parameter sample used is RandomParameterSampling. Random sampling supports discrete and continuous hyperparameters which could add to the versatility of the sampling. It can support early termination of low-performance runs. The policy used is the BanditPolicy with a slack_factor of 0.1. This policy terminates runs wherein the primary metric/s is not within the specified slack_factor which it compares from the best performing run. The SKLearn estimator uses TensorFlow and used the train.py as the entry script. 


## AutoML
The model generated by AutoML is easy to interpret and hyperparameters can be tuned. Also AutoML makes visible the core features that are driving the model.

## Pipeline comparison
The AutoML provides a more accurate model since it automatically handles the data. Its best model, which is named "amlbankmarket" and id: AutoML_27414687-1351-48c6-8d33-6308a0c78595_36, provides an accuracy of around 91.7328% compared to hyperdrive's 91.4421%. Though when working on it, more personalitzation could occur with optimizing the pipeline using Python SDK. There was a difference because the parameters like sampling and policy would somehow differ in optimizing using Python SDK.

## Future work
For future experiments, try aligning the code with consideration to the workspace name. Also keep checking the versions of the python for the compute cluster and the available sklearn versions. Using an AutoML experiment would also provide the best model in the most accessible way. 

## Proof of cluster clean up
<img src="delete compute.png">
