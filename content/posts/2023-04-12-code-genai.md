---
title: "Unveiling the Future of Code Generative AI"
date: 2023-04-12T11:29:09Z
tags: [ai, code generation, GPT4]
categories: [data engineering, data science, generative AI]
draft: false
---

Picture this: generating web or phone apps is no longer a daunting task - you can simply describe your desired functionality in plain English and watch as lines of high-quality code are generated before your eyes. The ability to understand, learn and create code using cutting-edge code Generative AI (GenAI) tools has far-reaching implications, such as dramatically reducing time and effort required for software development, allowing developers to spend more time on the more creative aspects of coding. Instead of manually researching how to use various libraries, developers can manage multiple AI bots that perform coding tasks for them using powerful Large Language Models (LLMs) built on state-of-the-art deep learning techniques and trained on vast datasets. With the ability to convert human language into optimized, high quality code with astonishing accuracy and speed, the future of coding looks incredibly bright and filled with amazing innovation.

AI models have progressed from only executing very specific tasks to more generalized, foundational models with in-context learning. From a coder’s perspective, some obvious functions of a text generation app are writing entire computer programs and explaining developer's code in real-time. Code GenAI produces working code that boosts a coder’s productivity, saves time on time-consuming tasks like handling APIs, generating boilerplate code, and reading entire legacy codebases. As a Machine Learning Engineer (MLE), I am very interested in how these code GenAI tools will be helpful to me and could evolve in the near future. Currently, these tools stand to help make my code more readable, testable and better documented.

### Brief History of Code GenAI State of the Art

In recent years, there has been an explosion of advances in deep learning approaches which has spurred interest in using LLMs for code generation, and several companies have developed tools that use these models to generate code snippets based on natural language prompts. While GenAI dates back to the 1950s, its evolution really accelerated with the publication of the Transformer neural network architecture by Google in 2017. It enabled large-scale training (for enhanced learning ability) and parallelism. Transformers elevated state-of-the-art NLP models by facilitating a two-part generative process: extraction of intent via natural language instructions and generating content according to human instructions.

On August 2021, OpenAI released the Codex model, a GPT model which translates natural language to code and powers GitHub’s Copilot. It was based on GPT-3 and fine-tuned on over 100 GB of code from Github repositories. It understands 12+ different programming languages such as Python, Javascript, Shell, and Go, which translates into faster iterations on games, web apps, legacy software and teaching.

Replit released Ghostwriter in 2022 and is uniquely placed to provide ML-powered coding recommendations with it's special dataset formed by watching seasoned and newbie programmers write software for millions of projects at character-level file granularity. Replit’s platform is unique because it tracks real-time keystroke and click data, character-level file changes and computing environment-related execution data.

Amazon’s CodeWhisperer (as of June 23, 2022) offers a similar paired programming experience to alternatives Copilot and Ghostwriter. Most recently, OpenAI released GPT-4 (on March 14th, 2023) and now holds the state of art for code generation on the HumanEval benchmark dataset for Python Coding tasks as well as competitive programming datasets such as Leetcode and Codeforce.

## Comparison of Code GenAI Tools

**Tool**| **User Interface**| **Capabilities**| **Base AI**| **Purported Value**  
---|---|---|---|---  
**Replit’s Ghostwriter v2**|  Only available on Replit web app (paid)| Aware of coding environment - help with creating, deleting files, fixing errors and handling entire tasks| Replit internal model initially based on Saleforce’s CodeGen model| Users of this product saved 30% of their time  
**Github’s Copilot**|  VS Code extension (paid) or JetBrains plugin and several others| Can autocomplete entire functions based on only a comment or a few keystrokes - more general purpose code tool| Powered by OpenAI’s Codex trained on publicly available source code| Massive productivity boost  
**Amazon’s CodeWhisperer (**[**source**](<https://aws.amazon.com/codewhisperer/>)**)**|  VS Code extension (free while in preview) or JetBrains plugin or AWS Cloud9 or AWS Lambda console| 

  * scan your code to identify security vulnerabilities and issues - generate small code segment recommendations based on their comments and code in the integrated development environment
  * “every time it generates code that is close to an existing snippet in its training data, it will note that and highlight the license of that original function” - handles Amazon-specific use cases related to using Amazon platforms very well

| 

  * No details on the model were readily available.
  * Trained on Amazon and open source source code.

| Improve developer productivity by generating code recommendations based on developers’ prior code and comments  
**GPT-4**|  Accessible via Web interface & API| Generates single or multiple lines of code from human prompting| GPT-4|   
[**CodiumAI**](<https://www.codium.ai/>)|  VS Code extension or JetBrains plugin (both are free)| Generate unit tests for your code - not general purpose code completion but focuses on code integrity| TestGPT-1 (fine-tuned GPT), static-code analysis methods, GPT 3.5 & 4| 

  * Get increased visibility of how changes affect the rest of code
  * Spend less time writing test cases - Easily find edge cases & make code more robust

  
**Tabnine (**[**source**](<https://www.tabnine.com/blog/announcing-tabnine-next-generation/>)**)**|  Lots of IDE integrations (full list [here](<https://www.tabnine.com/install>))| \- Whole-line and full-function code completions| 

  * “uses a family of a dozen of code-native models. The new code-native models are trained from the ground-up on code (vs. models pre-trained on text and retro-fitted to learn code). Each of these models is optimized from its basic “vocabulary” to fit a specific language and domain, thus using the entire learning capacity of the model for the relevant code patterns.”
  * Has 2 algorithms: “Public Code algorithm bases its suggestions on trusted public code with permissive licenses while the Private Code Algorithm adapts to you and your team's preferences, code selections, and ongoing AI interactions.”
  * Closed-AI model that only uses open-source code with permissive licenses for our Public Code trained AI model (MIT, Apache 2.0, BSD-2-Clause, BSD-3-Clause)

| “Our code-native models improve Tabnine by providing better precision and a 5x increase in the length of suggestions.”  
  
All Code GenAI tools cover the most popular languages such as Python and Javascript and many tools include other languages such as C#, Java, typescript, Ruby, Go and C++.

## Applications of Code GenAI

Code GenAI models can be used to prompt for creating new software in any programming language as well as summarizing and explaining code. I can imagine a product that uses code GenAI to reformat legacy repos- providing documentation and unit tests along the way. These kind of apps are really exciting because they enable continuous improvement of code with humans in the loop. Sharing code whether open-source or an internal enterprise project requires communication and collaboration with others in order to make the code robust (i.e. withstand errors) and accessible (across varied backgrounds and skill levels). Code needs to be readable, testable and rigorously documented to be accessible to other people, since coders often inherit code from others. This way of working also prevents coders from having to start coding from scratch, thereby saving time.

Applications of Code GenAI generally fall into one of four categories: code generation, code, explanation & understanding, transformation and autocomplete.

**code generation**

When the user provides a text prompt, the AI returns lines of code that was most relevant from its latent space. Boilerplate code is generated quickly from the model instead of from the coder, ready to be tweaked to the specific task right within the editor. New programs can be created in any language, saving time on researching APIs and libraries, and reading through the documentation.

**code explanation**

Users provide lines of code to the AI and ask it to explain or describe the code in text. A brief description of the highlighted code block could help programmers who are new to a repo or to the language readily comprehend the code sample. This text prompt could also be useful for subsequent code generation use cases.

**transformation**

This application is similar to code generation, however users can input code along with a text prompt to transform the input code into a better or alternative version of itself. Some examples include switching the coding style to that of another author or to be more consistent with a legacy repository.

**code autocompletion**

User input only code to the AI and receive only code as output, but without explicit guidance of a text prompt. This would work well for generating short snippets of commonly used or boiler plate code.

## Using Code GenAI Tools

Code GenAI offers various benefits to both junior and mid-level developers as well as data scientists. For instance, it can generate boilerplate code for initializing modern web apps that correctly connect to a REST API or library, without the need to consult documentation. This can help speed up the process of building web and mobile applications, enable rapid prototyping of software projects, and automate the process of generating optimized code for specific tasks. Additionally, Code GenAI can automatically detect and fix bugs in existing code, create custom algorithms for data analysis and machine learning, generate code for robotics and embedded systems, and leverage code generative AI for the development of distributed systems and cloud computing platforms.

Moreover, Code GenAI can be ingested into any web app with an API, allowing users to coordinate and execute instructions via natural language. For data scientists, this means they can dictate instructions that can be translated into code, much like telling Microsoft Excel to remove commas in cells. This market is poised for growth, with companies like [adept.ai](<http://adept.ai/>) positioned to capture it. Another benefit of Code GenAI is that it can create automated documentation in the form of docstrings and comments that can be converted to Sphinx documents. Developers can effectively treat their coding environment as a platform for interactive learning about a code base. Overall, Code GenAI offers a variety of features that can help improve coding efficiency and streamline the development process for programmers and data scientists alike.

The future of Software Engineering is super exciting with **at least** 100x boosts in productivity. We could see a single engineer manage dozens of software engineering autonomous AI agents that handle smaller coding tasks, such as git merge requests and commits, or generating performant code blocks. The revised software engineer’s primary job would be to interface with Code GenAI tools via prompt engineering (but without as many bugs and overall more precision). Future engineers may need to focus more on project management of many AI agents and code review to ensure high code quality and performance. Engineering teams may become smaller and more focused as Code GenAI enables productivity to exponentially scale - in the future, it will not take more people to execute a project faster. The relationship between team size and engineering output will decouple from a linear pattern into exponential as software engineering productivity increases by a few orders of magnitude.

### Limits

Code GenAI tools, such as Github Copilot, have made significant strides in assisting programmers with writing code beyond the simplistic autocomplete. However, there are still some limitations to their capabilities. Code GenAI tools require a significant amount of training data to generate code accurately, which means that their performance heavily depends on the quality and quantity of the training data available. As such, code GenAI may struggle with handling rare or edge cases, which could lead to suboptimal or incorrect code generation.

Secondly, code GenAI tools have limited understanding of context and may not always generate code that aligns with the programmer's intentions. They may produce code that is technically correct but does not fit the intended use case, leading to further debugging and rework. For synthesizing programs from docstrings, Codex solves 28.8% of the problems, while GPT-3 solves 0% and GPT-J solves 11.4%. However, Codex had difficulty with docstrings with long sequences of operations and relating operations to variables.

Thirdly, code GenAI tools may have difficulty with non-technical aspects of code, such as readability and maintainability. While they can produce functional code, it may not always be clean and easy to read or to maintain by other programmers, leading to growing technical debt and code quality issues.

Finally, code generative AI tools currently have limited support for some programming languages and frameworks. They may not be able to generate code for niche or legacy technologies, which could limit their usefulness for some projects. Several of these tools collect information such as the context of the file (code/comments) to make recommendations and may therefore feed proprietary code back to Replit, Github or Amazon. Without a closed code GenAI solution running on your company’s compute or explicit legal protections against leaks, some developers will resist keeping these coding assistants on work laptops. Some companies allow users to opt out of data sharing for service improvement and may be able to allay concerns of code leaks.

While code GenAI tools have made significant strides in improving the efficiency of programming, they are not a replacement for skilled human programmers. They still have limitations in their ability to understand context, handle edge cases, and produce clean, maintainable code. It's important for developers to use code GenAI tools to assist them, rather than relying solely on them for code generation. Effective real-world programming frequently involves managing extensive code packages across various locations, necessitating a comprehensive grasp of the software.

## Summary

Code GenAI is rapidly improving and has the potential to boost coders' productivity by automating foundational tasks, understanding legacy codebases, and generating optimized code. GenAI can be used to create custom algorithms for data analysis and machine learning, generate code for robotics and embedded systems, and create personalized user experiences in software applications. While the machines (hopefully) won’t be rewriting their core code and taking over the human world anytime soon, I predict that more developers will use a wide selection of code generation tools with increasing regularity. Considering all Code GenAI offerings, I am most closely watching Replit as I believe they are in the best position to roll out cool features based on their unique data.

**P.S.**

Replit is exciting because its mission is to onboard the next billion software creators by making coding more fun, collaborative and accessible. Imagine a world where you can easily optimize and digest other people's code all on your phone facilitated by browser-based dev environment. I have written about [using Replit and Binder](<http://datathrillz.com/binder-repl-it/>) before and still maintain that these tools are invaluable as learning aids and now more so than ever before. Replit is one of the only places you can take AI-generated code and run it without any installation worries.

#### Sources

  * [History of GenAI](<https://medium.com/artificialis/history-of-generative-ai-paper-explained-6a0edda1b909>)
  * [GPT-4](<https://openai.com/research/gpt-4>)
  * [Invest Like the Best Podcast with Amjad Masad](<https://joincolossus.us8.list-manage.compod/track/click?u=e35e149b66d5b7b476afc8ff5&id=cec89b17de&e=a3bba84333>)
  * [Stable Diffusion & Generative AI with Emad Mostaque](<https://twimlai.com/podcast/twimlai/stable-diffusion-generative-ai/>)
  * <https://blog.replit.com/fourth>
  * [Codex paper](<https://arxiv.org/abs/2107.03374>)
  * [Designing the Future of Software Engineering with Amjad Masad from Replit](<https://www.youtube.com/watch?v=bO0GunZCio8>)
  * [Amazon's CodeWhisperer](<https://techcrunch.com/2022/06/23/amazon-launches-codewhisperer-its-ai-pair-programming-tool/>)
