---
title: "Considerations for building a rules engine in Python"
date: 2021-09-29T08:47:08Z
categories: [data engineering, data science]
draft: false
---

I recently looked into how to implement a deterministic rule-based model on batches of data in Python and was surprised by the complexity of potential solutions I found. I want to implement a set of rules that when not obeyed will trigger an alert. It is basically a framework for applying a glorified set if-else/switch statements on different variables. Sounds simple, right? But not necessarily, depending on the customer’s needs. For instance, the solution becomes tricky if chaining these rules is needed which may create unpredictable system states. Let’s start by defining what a rule engine is and then discuss the potential rabbit holes that developers can fall into before delving in solution ideas. For several machine learning (ML) problems, we often need to first establish a baseline for making predictions. Without a baseline, how do we measure performance improvement or quantify when we need a new model? As a starting point to tackling data science problems, we can use heuristics or simplistic rules to establish this baseline. This allows us to directly embed domain knowledge into the solution, without spending lots of time training models. Usually, when tackling a data science problem, we get as much labelled data as possible and throw it into our favorite ML model for fitting, where the model’s parameters and hyperparameters are learned from the training data. However, there isn’t a formalized, general-purpose way of hard-coding rules from the domain expert into a machine learning model. When we take on a new data science challenge along with our business partners, we need to first establish baseline performance using a non-ML model such as a simple rule-based system. A rule engine is a set of production rules, which each has a criteria and an action. The rules are basically if-then statements that can be evaluated in any order. Rule Engines can be used as alternatives to or in tandem with more complex ML models (which is pretty common). For the purpose of this article, I will focus on the implementation of the rule engine, but people often use the term to mean a system that helps users (usually non-coders) build and evaluate rules. Other names for rule engines include expert systems, domain language systems or business rule policy. 

### Potential complexities of a Rule Engine

> **Implementing an Object-Oriented Programming Framework.** It is common to use Object oriented programming (OOP) to create a framework for establishing rules and applying expected actions. OOP seems like a good fit because we can express knowledge (or rules and facts) as classes. However, keep in mind that more complex joining of rules can make readability difficult and can exponentially impact performance.

> **Chaining of rules.** This is where the action of a single rule changes the system state in a way that changes the eligibility criteria for other rules, that is chaining may lead to unpredictable behavior. This is a more complex behavior for combining rules, which may make debugging and readability difficult. Additionally, it could indicate that it is time to pivot to a ML model as the cost of maintenance and design of a rule engine with several complex rules becomes too high.

> **Too many rules.** Similarly to the point above, a rule engine with too many rules can lead to unpredictable, opaque results. Sometimes adding a single rule or making a seemingly simple change can lead to unexpected consequences.

> **Whether the business (non-programmers) will need the ability to self-define rules.** If so, the business will need to easily learn and use domain specific language/syntax to express rules. This drastically increases the work required of the developer to facilitate this, e.g. a GUI may become necessary to facilitate ease of use for non-coders.

### Developing Rules Engine Solutions

Now that we have discussed the complexities of implementing a rule engine, we will delve into some solution implementation approaches. 

#### Solution Approaches

  1.      1. **_Extend the scikit-learn model framework_**
        1. Write fit and predict methods using the BaseEstimator class so that the rules-based approach is encoded as a model. This also gives the developer flexibility to leverage any methods from scikit-learn such as calling a proper random forest machine learning model if some criteria is not met. To learn more, see this [example for building a hybrid rule-based machine learning model using scikit-learn](<https://towardsdatascience.com/hybrid-rule-based-machine-learning-with-scikit-learn-9cb9841bebf2>).
     2. **_Write bespoke code for your specific domain_**
        1. This could turn into an unwieldy and time-consuming task so we will try to avoid writing as much code from scratch as possible. Additionally, this task may seem easy at first, but can quickly become more difficult as we consider the cost of deployment to production and our customer’s evolving needs which require a certain flexibility of code. Best-case scenario: you have easy to read code for your specific use case that is extensible and flexible. Worst-case scenario: you waste time implementing functionality that is already available and get stuck in the dreaded maintenance and documentation hole, without means of escape.
     3. **_Leverage other people’s code - don’t reinvent the wheel!_**
        1. There are several libraries on GitHub that we can use to help us along right now and thereby avoid developing a framework from scratch. At the very least, we will be able to ‘borrow’ ideas from the smart people out in the world who have tackled this problem before. [Here](<https://awesomeopensource.com/projects/rules-engine>) are some resources for Git repos for rules engines implemented in various programming languages (.NET, Java, etc.) and domains (cloud security, gaming, etc.).



#### Comparison of Python libraries for Rule Engines

| **Library** | **Description** | **Date of most recent update** | **# of Stars/Forks**  
---|---|---|---|---  
1 | [CLIPSpy](<https://github.com/noxdafox/clipspy>) | 

  * “Designed to facilitate the development of software to model human knowledge or expertise.”
  * stands for 'C' Language Integrated Production System
  * Originally developed by NASA
  * Considered state of art
  * Excellent documentation
  * Rules are loaded at runtime without the need to restart the engine

**_My thoughts:_**

  * _Syntax looks a bit hard to follow_
  * _May be overkill for simple rule engine needs_

| Aug 23, 2021 | 82 ⭐/ 16 ⑂  
2 | [Python Knowledge Engine (PyKE)](<https://github.com/e-loue/pyke>) | 

  * Powerful logic programming framework
  * Has own syntax for creating rules, which can be activated/deactivated on demand
  * Allows forward & backward chaining of rules

**_My thoughts:_**

  * _Has not been updated in 12 years which may indicate no support for any bugs found._
  * _Written in Python 2.5+ so I would stay away_

| Apr 26, 2010 | 76 ⭐/ 34 ⑂  
**3** | [**Durable Rules**](<https://github.com/jruizgit/rules>) | 

  * “for real-time, consistent and scalable coordination of events”
  * “can track and analyze information about things that happen (events) by combining data from multiple sources to infer more complicated circumstances”
  * “can be scaled out by offloading state to a data store out of process such as Redis.”
  * Forward chaining implementation
  * Supports multiple programming languages (Python, Node.js , Ruby)
  * Allows creation of rules and facts
  * C based implementation of RETE

**_My thoughts:_**

  * _I like that this framework implicitly facilitates scaling out to a data store_
  * _Good for a production system deployment with a development team that uses various languages_
  * _Fairly new and popular project_
  * _Syntax is easy to follow_
  * _Defines each rule as a new function_

| Sep 7, 2020 | 946 ⭐/ 185⑂  
**4** | [**Business Rules**](<https://github.com/venmo/business-rules>) | 

  * Python Domain Syntax language for implementing business intelligence rules without code
  * “simple interface allowing anyone to capture new rules and logic defining the behavior of a system”
  * Published by venmo
  * Express rule as JSON that can be generated from [this GUI](<https://github.com/venmo/business-rules-ui>).

**_My thoughts:_**

  * _Well suited to providing solution to non-coders in domains like marketing_
  * _Must define your base variables and actions as classes first, which may be unrealistic for expressing rules for many variables._
  * _Allows expression of labels of actions specified_
  * _I like that the rules and actions are very readable and optionally accept a label field_
  * _I wonder how fast it is and how well it scales, but appears promising_

| Mar 16, 2016 | 661 ⭐/ 203 ⑂  
5 | [Rule-engine](<https://github.com/zeroSteiner/rule-engine#:~:text=Rule%20Engine-,A%20lightweight%2C%20optionally%20typed%20expression%20language%20with%20a%20custom%20grammar,defined%20as%20strings%20in%20Python.>) | 

  * “A lightweight, optionally typed expression language with a custom grammar for matching arbitrary Python objects”

**_My thoughts:_**

  * _Great for rules using string, floats, datetime and compound (dict, list) data types_
  * _The debug REPL looks useful_
  * _Can match a rule to a single or multiple target objects (e.g. dicts or classes)_

| Aug 22, 2021 | 108 ⭐/ 14 ⑂  
6 | [PyKnow/Experta](<https://github.com/nilp0inter/experta>) | 

  * Python library for building expert systems, inspired by CLIPS

**_My thoughts:_**

  * _Documentation could be better as syntax is not super intuitive_
  * _May be overkill for rule checking needs_

| Seo 28, 2020 | 80 ⭐/ 107 ⑂  
_Table comparing top, relevant python libraries for implementing Rules Engines available on GitHub ([from the full list of repos](<https://github.com/search?l=Python&q=rules+engine&type=Repositories>)). Recency dates were extracted at the date that the post was written: 9/29/2021. The libraries that I think are most promising are bolded._ I will likely use the Business Rules or Durable Rules library, but many of the other libraries had functionality that I would consider incorporating into the final solution. All in all, I suggest putting the customer first in anticipating their current and future needs while considering the best implementation options for a rule engine in Python. Sources: [1](<https://martinfowler.com/bliki/RulesEngine.html>), [2](<http://www.mastertheboss.com/bpm/drools/what-is-a-rule-engine/>), [3](<https://towardsdatascience.com/hybrid-rule-based-machine-learning-with-scikit-learn-9cb9841bebf2>)
