---
title:  "Google Cloud 2018 Conference Highlights"
last_modified_at: 2018-03-20T16:00:58-04:00
categories: 
  - Conference
tags:
  - Google Cloud, Datalab, Dataproc, GPU, ML Engine, Cloud Storage, Google Cloud Best Practices
toc: true
toc_label: "Google Cloud 2018 Conference Highlights"
---

Conference Date: 07/24/2018-07/26/2018

## Key Conference Takeaways

### Key Initiatives for Google Cloud
* Standardizing around uniform software deployment using kubernettes.
    * Working towards on-prem kubernettes management from a google cloud portal. They’ve partnered with Cisco to try to deliver this by end of this month (August).
    * Incorporating Machine Learning and AI into everything:
        * AI/ML Services
        * Auto AI/ML
        * ML Engine
        * Kubernettes Kubeflow
* Orchestrate and Process all data within google cloud
    * Orchestration: Google cloud compose, Dataflow, Pub/Sub
    * AI/ML: Dataproc, Datalab, Dataflow, ML Engine, Big Query w/ ML
* ML/AI Use Cases, Common Practices
    *  New Common Practice: 
        * ML in practice should have an automated performance tracking and re-training mechanism. Data and model freshness should be a part of enterprise ML pipelines moving forward, and a backup plan should be in place for when a model’s performance gets low over time.
    * New Common Practice: 
        * Use ‘Kubeflow’ (A kubernettes based ML pipeline template) for developing and running ML pipelines. Kubeflow can then be used to deploy an ML pipeline on any kubernettes engine, whether on a laptop, on prem, on an edge device, or on a cloud kubernettes cluster.
    * Orchestration Use Cases:
        * Most use cases for Dataflow, Pub/Sub, and Cloud Compose deal with ingesting event or batch data, transforming it, and routing it to multiple storage containers or micro-services. For general job management
    * ML Use Cases (Where we would likely focus):
        * Most ML/AI use cases used Dataflow, Dataproc, Datalab, and ML Engine for gathering and training data, with Cloud Compose and Kubernettes running a query able micro-service for applying predictions with a trained model. Any data is typically stored either in the google cloud data store, or in cloud buckets. Some scenarios also fuse a static data store with information about some object (like a customer) and on the fly processing data (like what a customer is buying in a particular transaction) using a fusion of Pub/Sub and Dataflow.
* Product overviews
    * Google Cloud Compose: 
        * Built from apache airflow for managing job workflow graphs. A programmatic way to define workflows and jobs to be run in an automated fashion in the cloud. This is for managing general jobs, beyond data processing specific jobs.
    * Dataflow:
        * Built from apache beam. A distributed mechanism for building streaming and batch data transformation and enrichment pipelines. This is focused on designing and constructing data processing pipelines. 
    * Dataproc:
        * A fully managed cloud Hadoop/Spark cluster that can be spun up and down and is charged at a per-second usage (along with all hardware resources the cluster sits on top of).
    * Datalab:
        * A managed environment that you can write and run jupyter notebooks on, with computations occurring on cloud resources that have been set up previously (Like Dataproc). It is also commonly used at a visualization engine for data exploration (Has some pretty interesting features here) and for visualization and plotting.
    * ML Engine:
        * An API that allows for a user to submit Tensorflow based jobs with sets of parameters to be trained on google cloud resources.
    * Big Query:
        * An OLAP analysis-based data analysis system for performing processing over large amounts of data. It is meant as an analysis-based system, and continually pulling data out of it is considered an anti-pattern. Big Query now also has a set of ‘ML’ extensions for linear regression and logistic regression, but it isn’t very extensive or flexible. 

## Cloud Session Notes
* Session: Creating customer value with AI
    * Google is trying to make AI easy, fast, useful
        * Easy to build
        * Fast to build and use
        * Generating ROI
    * Problem domains
        * Generalized (ocado) personalized customer experience. Assessing sentiment of emails for automated responses. 
        * Demand forecasting and automated efficiency
        * Spotting patterns
        * Adding structure to unstructured language. Make sense out of images in box repository. 
                * 90% of data in a company is unstructured, so giving structure to this data is big.
    * Why use GCP AI?
        * Scale
            * Instant access to machines
        * Speed
            * Cloud TPUs and other HW
        * Quality
            * Pre-built services.
        * Customization
            * ML Engine for advanced solutions that are customized.
    * General levels
        * AI solutions
        * AI building blocks (Google AI services)
        * AI Platform (To train AI models)
        * Data & Analytics (Monitoring and visualizing)
    * General users
        * End users
            * Developers
            * Data Scientists
            * Business owners
        * Main Google focus
            * Sight
            * Language
        * AI Platform Goals
            * Train models
            * Build prod flow
            * Deploy anywhere
        * Adding Scikit-Learn, XGBoost support, Kubeflow
            * Kubeflow -> ML On Top of Kubernettes
            * On cloud and on premises deployment.
        * Google is investing in Kaggle platform for AI/DS community for development.
        * New services
            * Cloud Contact Center AI
            * Partner with IronMountain for document understanding (NLP) for docs stored with this partner.
        * Use cases
            * Ocado
                * Online grocer in the UK
                * Inventory/Demand prediction
                * Contact center efficiency
                * Immediate need contactability for emails (based off of NLP sentiment analysis)
            * Kerpie
                * Visual anomaly detection in food images.
            * Vice news
                * Use google translate for their purposes of content across the globe
        * General advice for ML
            * Google Platform
                * Fast prototyping
                * Datalab, Bigquery, Dataprep pipelines (DataFlow, Dataproc)
                * Easy Model Mangement
                * Easy Hybrid Deployment
                * Multi-Framework
            * Steps
                * Start Simple with simple problems and simple models
                * Google autofill search used a simple clustering model on an initial search query.
                * Start with business problem. Let the ML tools follow.
                * Integrate into Applications. End user doesn’t care about the tools, just the results.
                * ML can open you up to new interaction paradigms. Seek out and define these new dynamic paradigms.
                * Ex. Google search -> From key word search to question asking and commands.

* Session: Flexible Easy Data Pipeline with Google Cloud Composer
    * Mainly developed by open source community (Apache Airflow)
    * Overview:
        * New service that can be used for defining data processing pipelines. 
        * Initially, scheduling and managing gcloud jobs and pipelines is traditionally implemented by cron jobs, cron plus scripts (us), and finally-custom applications
        * GCP Composer is meant to make it easy to create/schedule/monitor a workflow. Now generally available (Generally available)
        * It is effectively a managed apache airflow.
    * Composer is a workflow orchestration engine and development framework.

* Session: Get smarter with Marketing and Customer Data
    * Problem:
        * Most data is located in a ton of data silos, and it isn’t integrated holistically.
        * 13% of orgs say they’re making the most of their available customer data.
        * Even Google sucks.
    * Prob example: Jane buys a TV. She keeps getting adds for TV after she’s bought, even from the same company.
    * Data sets
        * Store credit cards
        * Returns
        * Purchase patterns
        * Customer service resolution
    * The GCP data journey process
        * Collect, Transform, Analyze, Visualize, Activate
    * Guidelines
        * Get the business group in the same room as the data scientists
            * The stupid business questions are usually followed up with more interesting ones.
        * Cloud enables
            * Measuring across channels better
            * Forecast business results
    * Predict value of any interaction.
    * Predict what happens if I double investment in a product.
    * Predict what will happen to the business if an artist leaves spotify’s platform.
        * Identify and engage the right customers
    * This is the key goal: Learn and predict what customers care about, when they care about it, and what kind of help they need.

* Session: Machine Learning Made Easy: How to Build Flexible, Portable ML Stacks with Kubeflow and Elastifile
    *  Main Technologies
        * Kubeflow: ML based Kubernetes pipeline for multi-cloud solutions. (December of 2017). Version 0.1
        * Elastifile: Use for data portability alongside Kubeflow. (Vendor based solution). Better just to use google cloud storage bc this system is just an NFS file system (Aka, not really actually scalable)
    * Details/Notes
        * Two choices. Custom
        * Initially start with containers&kubernetes. Things don’t work from cloud to cloud. 
        * Cloud Native Apps: Declaritive microservice systems (Kubernettes)
        * Goal is to have a kubernettes solution for ML based pipelines in a general, generic way.
        * Transitioning from Experimentation, Training, Cloud is necessary.
        * Idea is to use Kubeflow as the unifying platform for building kubernettes based ML platforms. 
        * You really need data portability as well, because modern systems are inherently tied to the data computation system. Elastifile uses cloud connect, and elastifile cloud file system. (I probably wouldn’t use this because it is a vendor lock-in issue).

* Session: Continuous Deployment Platform for ML Models
    * Main Technologies
        * Design guide for continuous ML training. 
    * Details Notes
        * Continuous deployment in ML. Aka, continually training and deploying models over time.
        * Main session idea is about feedback. Need a feedback mechanism to keep the freshness of the ML model. Thus, need an ML refresh pipeline.
        * Example is the baby natality dataset. Training data from 1970’s to predict natality for 2008 is an issue, because the environment is changing.
        * To seriously use ML you have to keep tracking data over time, and need to keep your ML models fresh because the environment is changing over time. You need continuous test set generation, and a method for detecting when your model is over-trained, or is no longer generalizing well. By gathering data over time, we assume that we are moving towards a better understanding of reality.
            * Session: Hybrid Machine Learning: From the Cloud to the Edge
    * Main Technologies
        * Tensorflow, Tensorflow lite, Kubeflow
    * Details Notes
        * Areas of constrained compute
        * Workstations, laptops, mobile, IoT devices









