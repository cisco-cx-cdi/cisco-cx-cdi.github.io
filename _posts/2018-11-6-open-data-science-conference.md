---
title:  "Open Data Science 2018 Conference Highlights"
last_modified_at: 2018-03-20T16:00:58-04:00
categories: 
  - Conference
tags:
  - conference, active learning, bayesian optimization, bayesian statistics packages, continuous experimentation
toc: true
toc_label: "Open Data Science 2018 Conference Highlights"
author_profile: true
---

Conference Date: 11/2/2018-11/3/2018

## Key Conference Takeaways

1. “Software 2.0”
  * AI, and in particular deep learning methods, is very powerful. AI models can be viewed as another way to ‘write’ a program. Instead of using procedural code, you simply give the program the desired input/output combinations, and it learns the proper program matching the inputs and outputs.
  * To reliably and effectively develop “Software 2.0”, there needs to be a change in how development is approached. The following is a high outline of what was proposed:
        * Version Data Sets Used for Train/Test
        * Version Models
        * Use a ‘Test Suite’ to compare performance, and to continually check for proper behavior at edge cases
2. “Meta Learning Optimization”
  * AutoML using Bayseian Optimization was a common topic. New frameworks for distributed genetic algorithms for model architecture search were also presented. There were many talks on different ways to approach optimizing meta-parameters of models.
3. Explain-ability, Confidence, and Bayesian Methods
  * There were still many talks on Bayesian Statistics for explainable models with performance/prediction confidence bounds. Many python frameworks were talked about including ‘Pymc3’, ‘Sampyl’, ‘Pomegranate’, ‘Pyro Deep Bayesian Models by Uber’, and some others. We should keep an eye on these, as it finally seems there are some growing Bayesian statistical packages worth using (I just recently used pymc3 in one of our projects).

## Specific Talks

1. **“An Introduction to Active Learning”**
* Speaker: Jennifer Prendki, VP of ML at Figure Eight
 * Active learning is the process of ‘Intelligently Selecting’ data to be labeled from a set of unlabeled data. It is a sub-set of Semi-supervised learning, which focuses on how to use unlabeled data to augment and improve the learning process given a limited set of labeled training data. 
 * Active learning focuses on ‘query’ mechanisms for selecting the ‘most confusing’ or ‘most challenging’ data from a data set to label.
 * Active learning (and Semi-supervised learning) doesn’t give you more performance that supervised learning does if you had a sufficiently large labeled data set. Rather, it gives you higher performance given the same amount of labeled data, when labeled data isn’t totally sufficient for a task. 
 * Active learning and Semi-supervised learning causes a performance decrease in ~90% of papers published. This is attributed to the arbitrary selection of query strategies in these cases.
2. **“How Reliable are Machine Learning Benchmarks? A Reproducibility Study on CIFAR-10”**
 * Speaker: Ludwig Schmidt, PhD, Post-Doc at UC Berkeley
 * Most computer vision models are evaluated against the same test set year after year. This introduces a potential for over-fitting. In this talk, the speaker described how the way ML models are generally evaluated has the potential to cause “Overfitting through Adaptivity”. The idea is that you must perform ‘Reliability testing for a large number of adaptively chosen hypothesis (models) to perform hypothesis corrections’. (Methods to combat this in statistics are Benjamini Hochberg procedure, Post-selection inference, Differential Privacy,…)
 * He proposes that most machine learning methods must have the following to prevent overfitting through adaptivity:
        * Register a well-specified experimental protocol and analysis.
        * Collect data and evaluate according to pre-specified method.
        * Each new iteration of model testing/benchmarking, use a new test set generated from the pre-specified method. 
 * When evaluating the CIFAR benchmark, model performance ranking relative to each-other remains the same. Thus, in this instance, there isn’t overfitting through adaptivity. This is potentially explained by the ‘Ladder Mechanism, which is a method that guarantees no overfitting that was introduced in a paper by Avrim Blum (2016).
3. **“Experiments on AutoML in the Enterprise”**
 * Speaker: Erez Sali, PhD, Co founder, CTO, Firefly.ai
    * Focus on existing AutoAI packages for developing models. 
    * Most used packages are: *Auto sklearn, SMAC, Spearmint, RoBO*.
    * Most methods are just intelligent search or Bayesian optimization approaches. There are still may limitations to this kind of AutoML (And it somewhat differs from AutoML in the context of network architecture search for deep models).
4. **“Quantifying Uncertainty: Bayesian Data Analysis in Python”**
 * Speaker: Mat Leonard, Product Lead, Udacity
 * Main contention is that cross-validation validates nothing, pvalues are only useful if you can quantify your uncertainty in them (thus the pvalue distribution is more important than the value itself. Pvalue can be arbitrarily significant given its distribution. So, pvalues alone should not be trusted.)
 * If you approach modeling (At least in the linear sense) models using priors, likelihoods, and posteriors, you can generate parameter and prediction ‘credible intervals’ which can tell you things like ‘95% of the time, the prediction will fall into the range [x1, x2]’, which regular statistical confidence intervals cannot. 
 * We should think about applying this approach for the models that we have that are logistic regression models (It’s fairly straight-forward to do).
5. **“Continuous Experiment Framework at Uber” (https://eng.uber.com/xp/)**
 * Speaker: Jermy Gu, Senior Data Scientist, Uber
 * This talk focused on how Uber does “Continuous Testing” (A continuous, online, and adaptive version of A/B testing)
 * The speaker talks about how A/B testing can be costly when running the experiment has an ‘opportunity cost’ because of the waste in a test configuration that doesn’t work. By framing testing as a multi-armed bandit problem, and using a policy like Thompson Sampling, an A/B test can be changed to something that dynamically updates the distribution of which customers get which test configurations, and minimizes opportunity costs.
 * They have 4 use cases at Uber:
    1. Optimizing tests over the best email subject line to use. (Content optimization)
            * Email subject lines, in-app messaging, US campaigns, LATAM and EMEA Campaigns, Mobile/Web Design Optimization.
    2. Optimizing over the best models and parameters to use for a particular task. (Using contextual multi-armed bandits with Bayesian optimization)
            * Uber Eats Ranking
            * Recommendation System for Uber Trips
    3. Optimizing how uber performs spending.
            * Optimal bidding strategy
            * Optimal promo strategy
    4. Automating product feature rollouts.
            * Power and Risk based methods for deciding rollout percentage







