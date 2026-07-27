---
title: "Integrating Both Python & R into Data Science Workflows"
date: 2021-06-23T18:28:01Z
tags: [pipelines, Python, r]
categories: [data science]
draft: false
---

These days, I highly prefer coding in Python as compared to other languages that I previously used like Matlab or R. However, I have always wondered when data science teams should use one programming language over another for certain tasks. If all team members know R and Python equally well and need to train a machine learning model, which language should they use? How could they use both Python and R without redundancies? We will discuss how to best leverage both R and Python for building data science workflows.  Firstly, it really helps to know the strengths and weaknesses of Python and R. Python has overtaken R in popularity for machine learning, but R is pretty awesome at visualizing data as plots and/or dashboards. Deciding whether to exclusively use Python or R on a data science project is a big hairy topic and the answer depends on a number of factors, but [this article](<http://datathrillz.com/r-vs-python/>) provides lots of guidance to help data scientists make an informed decision. 

# **Leveraging R and Python in Data Science Workflows**

Using both R and Python in the same workflow requires more time and education, but also elevates 

  * Efficiency - by facilitating a potentially faster turn-around
  * Productivity - potentially adding business value and increasing output from the team

When you know both languages well or have team members with expertise in both R and Python, you can choose the best tool for the job at hand, instead of being limited to only one. One strategy is to use Python for the heavy lifting e.g. machine learning and then use R to build aesthetically pleasing, interactive scientific reports containing the model performance. 

# **Building Data Science Workflows in both R & Python**

Now let's dive into three ways of integrating both R and Python into a single workflow without sacrificing the functionality of one over the other. 

## **Call Python from R or vice versa**

One way of integrating R and Python is to call Python from RStudio (from within the RMarkdown file) because we can run chunks in Python, D3 or SQL from within the RMarkdown file. Reticulate is an R library that facilitates the use of both R and Python languages in a single RMarkdown document. Here are two different examples ( [example 1](<https://www.mango-solutions.com/integrating-python-and-r-into-a-data-analysis-pipeline-part-1/>), [example 2](<https://www.business-science.io/business/2018/10/08/python-and-r.html#part2>)) of data analysis pipelines. Instead of calling Python from R, you could call a command-line R script from Python using subprocess as seen in this [example](<https://www.kdnuggets.com/2015/10/integrating-python-r-executing-part2.html>).   

## **Flat File “Air Gap” Strategy**

The flat file strategy is the simplest strategy for integrating the two languages. We can use a flat file as an air gap between R and Pythons by taking the following steps:

  1. Refactor your R and Python scripts to be executable from the command line and accept command line arguments
  2. Output all shared data to a common file format like csv or xslx files. 
  3. Execute one language from the other, passing in arguments as required.

**Pros** | **Cons**  
---|---  
  
  * Simple method, so is often very fast to implement
  * Easy visibility of the intermediate outputs
  * Parsers for many common file formats already exist in R and Python e.g. CSV, JSON, YAML

| 

  * A common schema and/or file format needs to be decided at the start of the project. Excel is a popular file format that is human-readable, but versions changes can lead to inaccessible data or processing irregularities.
  * Can become cumbersome to manage intermediate outputs and paths if the pipeline expands considerably.
  * Consecutive reading and writing to disk can become a bottleneck if data becomes very large.

  
  
> **Considerations:** For the command-line R and Python scripts to be found, the executables must already be on your path. Otherwise the full path to their location on your file system must be supplied. Path names with spaces create problems, especially on Windows systems, and must be enclosed in double quotes so they are recognized as a single file path. In general for flat files, CSVs are a good format for tabular data, while JSON or YAML are best if you are dealing with more unstructured data (or metadata), which could contain a variable number of fields or more nested data structures. All these are very common [data serialisation formats](<https://en.wikipedia.org/wiki/Serialization>), and parsers already exist in both languages. In R the following packages are recommended for each format:
> 
>   * [readr](<https://cran.r-project.org/web/packages/readr/index.html>) for CSV files
>   * [jsonlite](<https://cran.r-project.org/web/packages/jsonlite/index.html>) for JSON files
>   * [yaml](<http://cran.fhcrc.org/web/packages/yaml/index.html>) for YAML files
> 
And in Python:

  *     * [csv](<https://docs.python.org/3/library/csv.html>) for CSV files
    * [json](<https://docs.python.org/3/library/json.html>) for JSON files
    * [PyYAML](<http://pyyaml.org/wiki/PyYAMLDocumentation>) for YAML files



## **Apache Airflow**

The third strategy for integrating Python and R is to use Apache’s Airflow to orchestrate the Python and R scripts. This approach is better suited to managing several, more complex scripts. Also, you may still need to use the flat file strategy to be successful. **Airflow** could be used to interchange R and Python as part of the pipeline. It only takes 15 min to set up, and tracks each script including failure status. Airflow also automatically saves results for each run, which is great for daily data ingestions and the need to regularly re-write data inputs & outputs. 

> Apache Airflow isn't the only game in town. There are several alternative pipeline libraries to consider like Luigi or Jenkins. If the pipeline is simple enough, you should consider using a Makefile to create a reproducible pipeline that tracks its dependencies. Make can be installed on both linux and Windows systems. 

When we have different components that are independent of each other, our code should be modularized (as functions and command-line scripts) to streamline the workflow. Generally, Data Scientists should use their preferred coding language for data exploration and/or early model development. This means quicker turn-arounds on evaluating the feasibility of the analytics solution. We have discussed how to get the best of both R and Python worlds in the same data science workflow. Thanks for reading! Sources:

  * [https://www.mango-solutions.com/integrating-python-and-r-into-a-data-analysis-pipeline-part-1/](<https://www.mango-solutions.com/integrating-python-and-r-into-a-data-analysis-pipeline-part-1/>)
  * [https://www.kdnuggets.com/2015/10/integrating-python-r-executing-part2.html](<https://www.kdnuggets.com/2015/10/integrating-python-r-executing-part2.html>)
  * [https://www.datacamp.com/community/tutorials/using-both-python-r](<https://www.datacamp.com/community/tutorials/using-both-python-r>)
  * [https://www.business-science.io/business/2018/10/08/python-and-r.html](<https://www.business-science.io/business/2018/10/08/python-and-r.html>)
