---
title: "Software Engineering as a Data Scientist"
date: 2021-02-20T17:37:51Z
tags: [SWE]
categories: [data science, deep learning, documentation, Software Engineering]
draft: false
---

Many of us in Data Science come from math, biology, chemistry or engineering or other non-Computer Science backgrounds, which may mean that we don’t have much experience writing and maintaining large code bases. Recently, I found myself getting frustrated with the structure of some of my code and searching for a better way to structure my code base. Let's explore some ways that we can improve our Software Engineering skills as Data Scientists!

## Improving Software Engineering Skills as a Data Scientist

To better structure my code, I implemented [object-oriented programming via classes](<http://datathrillz.com/using-classes-in-python/>) to help make my code easier to read and extend. Additionally, I used [decorators](<http://datathrillz.com/using-decorators-in-python>) to preserve original functions and methods while extending their functionality, instead of completely re-writing necessary callables. Rule #1 for software engineers: never repeat yourself. As Data Scientists, we should also aim to re-use as much of our previously written code as possible. One way to do this is by creating flexible, modular coding frameworks. Think about the scikit-learn library and how the fit and predict methods are used for training and generating predictions for most of the machine learning models. Instead of writing different methods for each model, scikit-learn has a uniform framework where each model is a class object. In order to introduce a new model, the developer just needs to ensure that the fit and predict methods fit into the scikit-learn framework. 

## More Software Engineering Resources

In my search for how to up my Software Engineering abilities, I found several resources helpful for shifting my approach:

  * [The Missing Semester of Your CS Education](<https://missing.csail.mit.edu/>) I love this course because it encompasses all the bits that are not explicitly taught in class, but are typically learned the hard way, i.e. long hours of frustration from trying something new and non-intuitive. While all topics are great, I found Debugging & Profiling, Metaprogramming, and Potpurri worth the time investment.
  * [Deep Learning Can Learn from Software Engineering](<https://event.on24.com/wcc/r/2709113/A797526F9AA558F0B778491FB85C23AF?>) by Jeremy Howard. Let’s apply Software Engineering to Deep Learning as it can be a complex beast with moving targets, especially when productionizing a model when you can expect your data distribution to shift. 
  * [10 things I wish I’d learned sooner about being a developer](<https://alexlakatos.com/coding/2020/11/17/ten-things-learned-ten-years-developer/>)
    * Ask for help
    * Let me Google that for you…
    * Keep Learning
    * Be a T-shaped person or Build T-shaped skills - 2-3 core skills of expertise plus have a wide knowledge base
  * [Production Oriented Code](<https://paulosman.me/2019/12/30/production-oriented-development.html>)\- Article on generating production-ready code, which can be a far cry from development code. A mental shift is needed to ensure Data Scientists don’t lose time when deploying models for production. 
  * [Beautiful Python Refactoring talk](<https://www.youtube.com/watch?v=W-lZttZhsUY>) at PyCon 2020 was illustrative of how to refactor in Python. It is simple, but powerful in demonstrating the Python code refactoring process. 
  * Read books on common software applications written by their developers. Check out the books called [500 Lines or Less and The Architecture of Open Source Applications](<https://www.aosabook.org/en/index.html>). Some of the topics that I found interesting were: Blockcode: A visual programming toolkit, A 3D Modeller, A Pedometer in the Real World, Audacity, Selenium WebDriver and The Hadoop Distributed File System. You can gain insight from the experts as a newbie so that you don't make the same mistakes. 
  * [visenger/awesome-mlops: A curated list of references for MLOps](<https://github.com/visenger/awesome-mlops>) \- learn more about Machine Learning Operations, basically DevOps for Machine Learning.
  * [Software Engineering Daily -Machine Learning Archives](<https://softwareengineeringdaily.com/category/machine-learning/>) \- a podcast about AI/ML from a software engineering perspective.

In this article, we have presented several resources for upskilling your Software Engineering as a Data Scientist, especially for those who have not come from a Computer Science background. This is the kind of learnings that can take years of experience to build practical knowledge, but hopefully with some focused reading and implementation, we can expedite our Software Engineering skills as Data Scientists.
