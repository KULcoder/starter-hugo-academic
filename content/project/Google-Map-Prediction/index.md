---
title: Google Map Place Rating Prediction
summary: Based on goole map dataset, predicting the rating of specific place by geographical and text data
tags:
  - Deep Learning
  - Data Analytics
date: '2023-02-01T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  focal_point: Smart

links:
url_code: 'https://github.com/KULcoder/Google_Map_Project'
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

# EDA

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

![MLP Confusion Matrix](images/mlp_cm.png)
