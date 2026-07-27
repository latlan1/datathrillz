---
title: "Creating Projects from Cookiecutter Templates"
date: 2021-01-25T18:09:45Z
tags: [cookiecutter, project, Python, pytorch, template]
categories: [data science, documentation]
draft: false
---

Ever want to generate a new repo based on a predefined template? Now you can using [Cookiecutter](<https://cookiecutter.readthedocs.io/en/1.7.2/README.html>)! I will show you how to easily spin up a fresh Cookiecutter repo for your latest data science project in Python.

Cookiecutter is an awesome command-line tool and Python package that creates projects (aka populates repo folders) based on cookiecutters (or project templates). What does this mean? Goodbye to manually copying and pasting old project repos. Now, you can automatically clone one of the thousands of cookiecutters or you can create your own.

## Why use Cookiecutter?

  * It is cross-platform - it works on any OS
  * Independent of Python with a simple command line interface (CLI) utility for installation and usage
  * We also love that it also supports various versions Python as a PyPI package
  * Supports any programming language or markup format e.g. Ruby, RST, Markdown, CSS, etc.
  * Directory names and filenames can be templated via Jinja2 by defining them in the cookiecutter.json file
  * Pre- and post-generate hooks - Python or shell scripts to run before or after generating a project.



Next, I will show how to create a project via the CLI based on the [modern-datascience cookiecutter](<https://github.com/crmne/cookiecutter-modern-datascience>) from installation.

![](/images/modern_datasci_screenshot_red.png) This Cookiecutter has a bunch of helpful folders for structuring your data science project - good for keeping track of documentation, pre-commit hooks, & unit/functional tests.

## How to Create Your Project via CLI

  1. Install cookiecutter via command line tool (don't forget that Git needs to be installed to successfully use Cookiecutter)
  2. Clone your Cookiecutter project template


[code] 
    $ git clone git@github.com:crmne/cookiecutter-modern-datascience.git
[/code]

3\. Modify the variables in the cookiecutter.jso

You can define your project name in the json file.

4\. Change up the skeleton project (if desired)

5\. Generate your project based on your cloned cookiecutter
[code] 
    $ cookiecutter cookiecutter-modern-datascience/
[/code]

Next, we will show an alternative way of creating a project but with Python instead of command line. 

## How to Create Your Project via Python

  1. Install the Cookiecutter Python package


[code] 
    $ pip install -U cookiecutter
[/code]

2\. Generate your project from a local cookiecutter or GitHub
[code] 
    from cookiecutter.main import cookiecutter
    
    # Create project from local template
    cookiecutter('cookiecutter-modern-datascience/')
     
    # or Create project from git repo template
    cookiecutter('https://github.com/crmne/cookiecutter-modern-datascience.git')
    
[/code]

In conclusion, you can set up your project using CLI and Python. Now, you are all set to start your data science project can begin with filling out the README. Check out this [Writing Awesome READMEs article](<http://datathrillz.com/writing-awesome-readmes>) if you need some guidance.

Additionally, if you develop apps, you can use Cookiecutter to set up template repos too! Just find your favorite cookiecutter template by searching GitHub + [your programming language/tool e.g. Rust, PyTorch, Android, React, etc. ]

For example, some Cookiecutter templates that I look forward to using are:

  * Flask Skeleton - Flask (web application) starter project with or without Docker
  * PyTorch - Clear template for PyTorch Deep Learning Projects
  * FastAPI - Flexible general-purpose template for your API
  * React-Django - Template for modern, full-stack (React.js as frontend & Django as back-end) web applications with linting & testing
  * Click App - Starter for creating new Click command-line tools



Sources: [Cookiecutter Usage Help](<https://cookiecutter.readthedocs.io/en/1.7.2/usage.html>), [Modern Data Science Cookiecutter Git](<https://github.com/crmne/cookiecutter-modern-datascience>)
