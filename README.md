# Fewshot text classification with meta learning and BERT
## Requirements
  - transformers==2.2.1
  - python>=3.6
  - torch==1.3.0
# Solution 
We leverage data from high-resource domains to create a good "starting point". From this point, we start training a specific model for low-resource domain.

## Approach 1: Transfer learning
We train a single model (Model_X) on concatenated data from high-resource domains. Then, we retrain Model_X on low-resource domain

## Approach 2: Meta learning
We stimulate a lot of situations where the Model_X are forced to learn fast with limited training datad. The model_X are getting better at "learning with less" after each training situation. We called these situations as Meta-task. Each task contain two sets:
 - Support set: contain few training samples
 - Query set: Provide learning feedback. The model use this feedback to adapt its learning strategy
 
There meta tasks is constructed from high-resource domains, serving as meta training data.

So, what is the form of "learning strategy" of a learner ? . It's simply an initialization of weights.
 - A good learner (learner that learn fast and obtrain good result on test-set) have a good initialization of weight, which can be easily tunned on data from new domains.
 - A bad learner simply have a bad initialization of weights.

In other words, meta training is simply a process of learning to initialize model's weights such that these weights can be easily tunned. 

