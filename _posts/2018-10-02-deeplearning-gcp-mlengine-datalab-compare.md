---
title:  "Deep Learning on GCP: Datalab vs ML Engine"
last_modified_at: 2018-03-20T16:00:58-04:00
categories: 
  - Best_Practices
tags:
  - Google_Cloud, Datalab, Dataproc, GPU, ML_Engine, Cloud_Storage, Google_Cloud_Best_Practices
toc: true
toc_label: "Deep Learning on GCP: Datalab vs ML Engine"
---


## What is ML Engine?

'ML Engine' is am service that google supports that allows a developer to run both 'training' and 'serving' jobs using google's resources for ML models. ML Engine is a service that can be called for on-the-spot training of a tensorflow, XGBoost, or now (Think it's till beta) scikit-learn models. The service provides the option to train a model using GPUs, TPUs and other resources. The service purports to be an on-demand and 'pay as you use' methodology for training machine learning models. More about the service can be learned here (https://cloud.google.com/ml-engine/docs/tensorflow/getting-started-training-prediction). 

## What is Datalab?

'Datalab' is an automated set of 'configurations' that have been written by google, that can be started up on any google cloud compute instance. Technically it is a 'Docker' container (More info on docker here: https://docs.docker.com/get-started/, TOTALLY LEARN IT!!!), which is why the configuration run on any google cloud compute instance. Datalab includes configurations for a datascience environment, as well as utilities for visualizing data sets. It also acts as a general 'drop in' for python 'jupyter' notebooks. Google's documentation about datalab can be found here: https://cloud.google.com/datalab/docs/quickstart.

Our team uses datalab in two main ways. The first main way is to run datalab in its own instance on google cloud compute. This method is the simplest for quick jobs, or when you need a dedicated GPU environment for running your code. Since this method starts datalab on its own instance, it does not natively have access to any spark computing clusters. However, an individual datalab instance can be connected to a remote spark cluster. The second method can be used when you need dedicated GPU, CPU, or RAM resources for running your code. It provides a quick and fairly simple way to spin up an instance (although it takes around 11 minutes to spin up) where you have dedicated access to everything. The downside here is that the remote connection to the spark cluster through a jupyter notebook is somewhat finicky. For example, imports of packages must be made from within the cell that will run on spark if you have custom packages to run. There are some potential ways around this (create an import_func() that simply imports all packages, and call that at the beginning of each cell that will run on spark).

## What are the ways we train 'Deep Learning' based models on GCP?

* Attach a GPU to a Datalab instance. (Our team preferrs this at the moment)
* Train by sending a model and data to 'ML Engine'.

## Why do we currently prefer to attach a GPU instead of call ML Engine?

Our team prefers enabling GPU based deep neural network training by attaching a dedicated GPU to our datalab or dataproc master instances rather than trying to utilize ML engine. There are many reasons for this, including ease of use, reduced lost developer time,and avoiding the hacky method to train models in a notebook. The reality of ML engine is that the service's design implies that you simply build a model once, and then train it, and then deploy. As we all know, this is not the truth, and you often iteratively improve a model's performance. Thus, being able to alternate between making a change in your model and training it quickly and seamlessly is very important. It's possible to do this with GCP, but only in a very hacky way (aka, structuring the actual model code as a python package with its own setup file, using  %%writetofile to write a model from a jupyter notebook,  and %%bash to ship pre-processed data to google cloud buckets, to run the google cloud ML Engine command line command to train the model from within a jupyter notebook, and again using it to download the trained model back to the local notebook). While configuring projects like this might be a good practice to move towards as we develop new models, it's currently not a very advantageous use of time and resources, unless code requires TPUs to be able to iterate on model development.

## Guides for Both Methods

### Terminal only method of training with 'ML Engine'

Quickstart Guide: https://cloud.google.com/ml-engine/docs/tensorflow/getting-started-training-prediction

### Training on 'ML Engine' from within a notebook

Packaging the python code for training: https://cloud.google.com/ml-engine/docs/tensorflow/packaging-trainer

Running the custom code from within a jupyter notebook (Follow this tutorial): https://github.com/GoogleCloudPlatform/training-data-analyst/blob/master/courses/machine_learning/deepdive/06_structured

### ML Engine Guides: (https://github.com/GoogleCloudPlatform/training-data-analyst)

* Custom python model packaging (Can be done from within a notebook):
    * https://towardsdatascience.com/how-to-train-machine-learning-models-in-the-cloud-using-cloud-ml-engine-3f0d935294b3
* Good Example Code:
    * https://github.com/GoogleCloudPlatform/training-data-analyst
    * (Some examples of full jupyter notebook based method of training and deploying models) https://github.com/GoogleCloudPlatform/training-data-analyst/tree/master/courses/machine_learning/deepdive/06_structured
* Example end-to-end model training and deployment:
    * https://codelabs.developers.google.com/codelabs/cloud-ml-engine-image-classification/index.html?index=..%2F..%2Findex#0
* Cloud ML Samples:
    * https://github.com/GoogleCloudPlatform/cloudml-samples/
* Python Client API Guide
    * https://cloud.google.com/ml-engine/docs/tensorflow/python-guide


























