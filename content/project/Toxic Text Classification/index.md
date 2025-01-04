---
title: Fine-tuning LLAMA 1B with LORA on Toxic Text Classification
summary: Using Jigsaw Dataset, predicting if a comment is toxic with popular methods.
tags:
  - Deep Learning
date: '2024-12-01T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  focal_point: Smart

links:
url_code: 'https://github.com/KULcoder/Toxic_Text_Classification/'
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
(Detailed methods and results can be found in the source code.)

Constructing...

# Intro
Text classification is a classic NLP task. As different strong & new models being developed, I tried some popular choices of models doing text classification. My ultimate target is testing: is it practical to fine tune a LLM and use it to do text classification on local machine? I test this with toxic comment classification task, which is quite useful in maintaining a healthy internet environment.

# Data
I used the [toxic comment classification chllenge](https://www.kaggle.com/competitions/jigsaw-toxic-comment-classification-challenge) data on kaggle. This dataset is made up with a large number of Wikipedia comments which have been labeled by human raters for toxic behavior. There are many types of toxicity, but for simplicity I only considered the basic `toxic` feature.

Moreover, I only used those English comments as other language comments are too less in amount, and causing the vocabulary size to be too huge. Also as the data is highly imbalanced toward non-toxic data, I balanced the training data by down sampling the negative comments.

# Models

## LSA
The first model I choosed is [tf-idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) vectorizer + truncated [SVD](https://en.wikipedia.org/wiki/Singular_value_decomposition) + logistic regression, which is known as latent semantic analysis. This method is very effcient and popular at a relatively early age of NLP. 

## Word2Vec
The second model I choosed is to use classic [word2vec](https://arxiv.org/abs/1301.3781) method developed in 2013 as a very important method of representing words into vectors. For this project specifically, I trained my own Word2Vec embedding. Later I averaged the word embeddings in a sentence (same concept used in deep average network) and feed it into a logistic regression model.

## BERT
After transformer being developed, [BERT](https://arxiv.org/abs/1810.04805) and its variants become the state of the art models for doing text classification tasks. BERT, brief saying, is the encoder part of transformer architecture. I downloaded the pre-trained BERT and fine-tuned it for this task.

## LLAMA 1B with LORA
One specific trend in NLP nowadays is to use one unified model for all types of nlp tasks. But how can we use LLM to do text classification? I pick META's recent release LLAMA 3.2 (September 2024) 1B model, I designed a prompt to ask for direct answer whether a comment is toxic or not. With this prompt, I used the LORA to finetune the model for our task.

# Results
## Performance
|          | Train Acc | Test Acc |
| -------- | --------- | -------- |
| LSA      | 85.44%    | 84.65%   |
| Word2Vec | 86.21%    | 85.83%   |
| BERT     | **96.55%**    | 93.52%   |
| LLAMA 1B | 95.57%    | **94.94%**   |
### Confusion Matrix LSA
![LSA Confusion Matrix](images/CM_LSA.png)
### Confusion Matrix Word2Vec
![Word2Vec Confusion Matrix](images/CM_Word2Vec.png)
### Confusion Matrix BERT
![BERT Confusion Matrix](images/CM_BERT.png)
### Confusion Matrix LLAMA 1B
![BERT Confusion Matrix](images/CM_LLM.png)
## Run Time

# Discussion

<!-- # EDA

## Business Rating Maps
Unveil a geographical distribution of business ratings.
![Business Rating Maps](images/business_rating_maps.png)

## Review Word Cloud
Visual representation of frequently mentioned words in reviews.
![Word Cloud](images/word_cloud.png)

# Model Pipeline

We begin by encoding the review text data using [TF-IDF](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html). This encoded data undergoes dimension reduction through PCA. Subsequently, the transformed data feeds into two different models: Random Forest and Multi-Layer Perceptrons.


# Results

## Random Forest
**Test Accuracy Score**: 44.24%

![Random Forest Confusion Matrix](images/rf_cm.png)

## Multi Layer Perceptrons

**Test Accuracy Score**: 65.37%

![MLP Confusion Matrix](images/mlp_cm.png) -->
