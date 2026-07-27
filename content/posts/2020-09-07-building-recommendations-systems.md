---
title: "Building Recommendations Systems"
date: 2020-09-07T18:00:48Z
tags: [collaborative filtering, pytorch, recommendation sytem]
categories: [data science, deep learning, machine learning]
draft: false
---

Recommendations systems are good for matching users to their favorite products and are incredibly popular. In fact you have likely used a recommendation system at least once in your life. For example, Amazon uses recommendation systems to suggest new exciting products to purchase based on users' previous purchase patterns and those similar users. Netflix also utilizes recommendation systems to suggest new TV Shows and movies. 

Before we get into recommendation systems, it is important to briefly cover two general-purpose approaches for identifying target customer groups and making product recommendations. These two approaches are called Clustering and Association Rules. 

## Clustering Algorithms

  * General purpose approach for identifying target groups without pre-labeled data
  * Good for finding entities that are closest together but distinct from others
  * K-means and hierarchical clustering are pretty common



## Association Rules Learning 

  * Good for determining which items appear together in a 'basket/cart' scenario
  * Rules are in the form ‘if X then Y’
  * Best for market basket analysis



Now that we have a bit of background and know what recommendation systems are, let's explore the various types and how to build them using PyTorch. Recommendation systems will suggest items suited to a specified user or will predict the ratings of items. There are three approaches to building recommendation systems: Content-based filtering, Collaborative filtering and Hybrid (combines both approaches).   

## **Content-based Filtering**

  * Estimates the item rating based only on the user and product features 
  * Other products and users are not considered in this approach
  * Does not work as well as collaborative filtering
  * Good for system with a few users
  * Requires rich and accurate product data
  * Hard to extend across products
  * Domain specific recommendations



## **Collaborative Filtering**

  * Employs information about other users and products in order to recommend highly rated items
  * Enables personalized recommendations based on aggregation of users’ behavior
  * Assumes that users who liked items in the past will like similar items in the future = people who buy X will also buy Y
  * Don’t need huge amount of metadata on products
  * Requires users’ historical preferences or ratings on items e.g. star ratings by users (explicit) or clicks, page views (implicit ratings)
  * **Nearest Neighborhood Approach** : 
    * Tries to find similar users (user-based collaborative filtering) or products similar to those previously liked (product-based collaborative filtering) 
    * Calculate similarity between users and/or products
    * Not widely used because user data tends to be sparse, which neural networks don't handle well
    * Not computationally efficient
  * **Matrix Factorization** **Approach** : 
    * Outputs a score for every combination of user and product (as the rating matrix,R)
    * For R, rows are Users & columns are Products
    * Entries are sparse because User i may not have bought/engaged with Product j and will need to be estimated
    * Use Latent Factor Analysis to estimate R matrix and thereby identify hidden factors that drive the relationship between users and products
    * Utilize the Alternating Least Squares (ALS) algorithm to find decomposed matrices (one is for products x latent factors and other for items x latent factors) without having the rating matrix, R
    * May need to add regularization to prevent overfitting due to the large number of parameters we are estimating and enable generalization to real-world data 
    * Weighted regularization (WR) adds a penalty term to the loss function to stop parameters from growing too large
    * The evaluation metric Mean Average Precision (MAP@k) tells how well, on average across all users, the top k recommendations were; dependent on the order of recommended items; its is range 0 to 1, where higher implies a better model 
    * Loss metric: RMSE



## Building Recommendation Model in PyTorch

  * The Embedding Layer 
    * a dense matrix-type representation and distinct from regression Linear layers
    * Initialized at random then trained along with other neural network layers
  * 1st embedding layer dimension must be divisible by 2 since half is dedicated to user ratings and other half to the item ratings
  * At the end of training, embeddings for similar users and similar items will have close values
  * Training the model:
    * For each batch of data (containing users, items, ratings):
      * Make model prediction of ratings using users, items
      * Calculate loss between predictions and actual ratings & update tally of epoch loss
      * Calculate gradient and update the model parameters
