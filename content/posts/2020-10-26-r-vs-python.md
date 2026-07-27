---
title: "R vs Python"
date: 2020-10-26T21:13:35Z
tags: [python capabilities, r vs python]
categories: [data science, machine learning]
draft: false
---

I generally reach for Python when building data science pipelines, however I discovered R before I decided to invest in learning Python. R has saved me lots of time when it came to quickly and easily preparing nice-looking plots for research. It begs the question of where is R better than Python for certain purposes?  We will discuss the benefits and downsides of Python and R so that we can reach for the appropriate tool when needed, instead of treating all problems like nails when a screwdriver is required. 

Ultimately, anyone could build data science workflows exclusively in R or in Python with enough time/expertise, but there are certain use cases where one language may be advantageous over the other. Before choosing a tool, individuals should consider:

  * Tools commonly used in their field - this may dictate availability of repos or external forums that can be consulted for help toward getting the task done efficiently.
  * Tools used by colleagues/team - using the same tools means that code can be shared and simpler tool stack overall.
  * Cost of learning a new language - it can take years to effectively learn a new language that solves the problem. 

**R**| **Python**  
---|---  
Great for stats, data analysis/exploration and visualization. Interactive & aesthetically pleasing graphics/dashboards. | Seaborn and plotly are great data visualization libraries with similar (but fewer) plotting  capabilities. Visuals are not as informative. (This is rapidly changing!)  
Excellent Reporting tools e.g. RMarkdown (multimedia, journal quality report) and Shiny (fast prototyping of interactive web apps).  | Has Jupyter Notebooks, but capabilities offered are limited compared to R. No Shiny equivalent.   
Rooted in Stats, developed for researchers and scientists to design, perform and communicate data analysis results.| General purpose with roots in computer science and math. Useful for tasks beyond data analysis.  
Catching up to Python in this space| Excellent data science libraries for NLP and deep learning e.g. TensorFlow, scikit-learn, and web frameworks libraries for scripting websites at scale.  
| Better for Web scraping and crawling, and database connections.  
| Faster computations and import of large input files. Good for mathematical computation and understanding algorithms  
| Production - ready language  that can integrate all parts of the workflow. High ease of deployment and reproducibility.   
Easy to learn for folks with little to no coding experience, but more difficult to develop expertise in due to advanced functionality.| Folks with a computer engineering background will find Python easier to learn. It has a linear learning curve.   
Many ways of writing the same functionality.| More consistency in the way code is written (i.e. pythonic way of writing code).   
  
Python leads R in overall popularity and is projected to completely overtake R in terms of usage in the future, making it the safer tool to use going forward. 

![](/images/stackoerflow_trends_prog_lang.png)Stack Overflow Trends in popular programming languages since 2008 ([Source](<https://insights.stackoverflow.com/trends?tags=java%2Cc%2B%2B%2Cpython%2Cjavascript%2Cruby%2Cr>))

R is great for early exposure to coding and for learning statistics especially while taking a course due to its extensive statistical libraries. However, as a budding data scientist builds their coding expertise and moves toward creating production-ready machine learning models, Python becomes the better choice.
