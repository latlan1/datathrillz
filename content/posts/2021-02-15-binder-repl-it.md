---
title: "Binder & Repl.it"
date: 2021-02-15T17:18:46Z
tags: [courses, Python tools, teaching]
categories: [python hacks, soft skills]
draft: false
---

I recently discovered two great tools for easily creating interactive coding environments without installing a thing. These tools facilitate sharing of code in multiple languages and are wonderful resources for demonstrating programming concepts when teaching a course. 

# **Binder**

The first tool is called Binder, is open-source and was released in 2017. It is awesome because it allows data scientists to share their work in Python , R or Julia in a reproducible manner. Binder can be configured for Python (Anaconda or pip environment) and R (using RStudio and/or Shiny). Multiple user interfaces can be specified. For example, for Python we can use a terminal or Jupyter notebook in the repo.

## How it Works

![](/images/binder_how_it_works.png)

## Common Use Cases

### Create Live Demos

Share interactive demo with a group of people who can engage with the demo in real-time. You can create interactive presentations with RISE. Binder is good for sharing presentations, demos or tutorials. One cool example of Binder is for the use of multi-language demos. Here is [a R and Python binder](<https://github.com/binder-examples/r_with_python>): ![](/images/binder_snip_red.png) Inside of the Binder, you can find several files: 

  * python_example_for_Jupyter.ipynb - Notebook file using a python kernel for working in Jupyter
  * R_example_for_Jupyter.ipynb - Notebook file using an R kernel for working in Jupyter
  * python_example_for_RStudio.Rmd - RMarkdown file with python code chunks for working in RStudio
  * R_example_for_RStudio.Rmd - RMarkdown file with R code chunks for working in RStudio



### Open Source Package Documentation

Binder can be used to facilitate real-time coding environments as an introduction to new libraries. [spaCy](<http://spacy.io>) is a Natural Language Processing Python library that has editable code windows facilitated by Binder, which allow users to play with spaCy modules in Python.  ![](/images/spacy_example.png) This is a highly effective way of teaching new users by demonstrating and testing the capability of spaCy. Users can quickly interact with new features, and APIs. With Binder, you can [build documentation from Python examples/notebooks and create a visual gallery](<https://sphinx-gallery.github.io/stable/index.html>).

### Scientific Research & Reproducibility

Use Binder for quickly sharing DS work on a specific dataset based on your latest repo. This sounds appropriate at internal DS team presentations or updates and could allow other team members to directly engage with or piggyback off of already established analyses and visualizations. 

### Textbooks & Teaching

Binder allows the fast spinning up of a controlled platform for newbie coders or learners to explore. Some [fun examples of Binders](<https://mybinder.readthedocs.io/en/latest/examples.html>) that I liked were the Deep Learning workshop, Signal Processing, and Intro to numerical computing for Kids. Binder gives users the ability to expedite sharing course content and educational material. If you teach using Jupyter Notebooks, [you should consider incorporating Binder.](<https://jupyter4edu.github.io/jupyter-edu-book/>) Check out [Binder’s Usage page](<https://mybinder.readthedocs.io/en/latest/using.html>) for more examples.

# **Repl.it**

The second tool is called Repl.it - a collaborative IDE in your web browser for coding in Python, C++ and 50+ other languages. REPL stands for read-evaluate-print loop. Repl.it lets you code with installation or versioning issues quickly and easily. It is particularly great for coding beginners or team coding assignments. There is no file installation setup, just code, collaborate and share.  ![](/images/replit_snip_red.png) Repl.it has 3 pricing tiers: Starter, Hacker & Teams. The Starter tier is free and comes with 500MB of storage and memory (each), 0.5 vCPUs and multiplayer collaboration in a public repl. That’s not bad for tinkering with friends or colleagues. The Hacker & Teams tiers are really aimed at teachers and corporate coding teams. Repl.it is used to teach various topics in online Python courses. It is great for first-time exposure to Python.  I found a few cool games coded in repl.it: ![](/images/defuse_the_bomb.png) [Defuse The Bomb (CSS, HTML, JS)](<https://repl.it/talk/share/Defuse-the-bomb-New-Part-added-explosion-sound-effect-now-added/120501>) \- open the game up in a new tab, press play to try to defuse the bomb by guessing the correct 4 integers. If you don’t guess the code in time, it’ll explode (sound effect included). [Tic-Tac-Toe Game (Python)](<https://repl.it/@CodingCactus/Tic-Tac-Toe>) \- you can play against the computer or person.  You can find more cool repl.its at the [rep.it community share website](<https://repl.it/talk/share>).  In summary, we’ve discussed two tools for learning, collaborating and teaching Python. Both tools are invaluable when illustrating programming concepts as well as pretty cool and fun. They also have growing user bases that make the tools easy to learn and setup.
