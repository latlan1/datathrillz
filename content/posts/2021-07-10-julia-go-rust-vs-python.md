---
title: "The next coding frontier- comparing about Julia, Go & Rust with Python"
date: 2021-07-10T19:05:33Z
tags: [learning go, using julia, using rust]
categories: [data science, machine learning]
draft: false
---

Currently, Python is the dominant programming language of data science and machine learning and is popular for more general scripting. It’s pretty awesome compared to its predecessors like C/C++, FORTRAN due to its ease of use, flexibility and readability. Python also has an active and robust library culture after over 30 years of existence. However, Python has some weaknesses that newer languages like Julia, Go and Rust readily address. 

# **Pythons Challenge Areas**

![](/images/SLOW.png)

### Python can be slow. 

Compared to C and FORTRAN and most recently Julia, Python is pretty slow. This is a big deal when processing millions of petaflops is concerned such as training massive deep learning models with millions of parameters. Python is slow due to it being an interpreted language, meaning it must be interpreted before it is compiled to executable machine code. Alternatively compiled languages don’t require interpretation and are simply compiled to machine code. As such, deployment as a single binary requires the interpreter, libraries and other dependencies.

![](/images/testing.png)

### Python requires lots of testing. 

This is due in part to only allowing dynamic typing, which means that variables are designated as a float or boolean at run-time. Languages such as C, FORTRAN and Julia have static typing which saves time on unnecessary testing for bugs caused by unexpected data types. 

## Julia

Julia is targeted at an audience that wants to code mathematical concepts, machine learning, data mining and linear algebra. It is a versatile language that is faster than C. It has extensive code conversion capability, which will help adoption without sacrificing productivity. You can run C and Python code in Julia as well as run Julia code in Python. Julia is primarily a functional programming language that compiles at run time very fast. Julia programs can generate other Julia scripts in a similar way to Lisp. It has an awesome debugger that allows users to step through functions and inspect variables. 

The creators of Julia were quite ambitious in their goals to birth a language that captures the dynamism of Ruby, general programming like Python, intuitive for statistics like R, adept at string processing like Perl and great at gluing programs together like shell. They also strived to make Julia easy to learn, fast and interactive. ** __**

### Who will appreciate Julia: 

  *     * Folks that like math-friendly syntax, such as Matlab and Wolfram Mathematica, but with an open source culture.
    * Want fast execution compared to Python.
    * Want intuitive, large-scale machine learning, statistics and linear algebra.
    * Likes the benefits of combining dynamic typing and static typing.
    * Want easy package management
    * Want parallelism without serializing data and de-serializing between threads or nodes.



## **_Go_**

Golang or Go is a modular, compiled language for software development. It addresses the disadvantages of using C/C++, such as injecting bugs and security vulnerabilities by incorrectly or unsafely accessing memory. Go can also be used for general purpose programming e.g mobile apps, distributed micro services and embedded microprocessors. It has wide commercial support and a user base with thriving libraries. It was designed as a simple language with few keywords and little syntax.

### Who will appreciate Go: 

  *     * Your projects require speed and lightweight code deployed as a binary. 
    * Value clear code over fast code. 
    * Very easy to learn due to simplicity. 
    * New developers can learn a new, large code base quickly. 
    * Want to manage high scale, concurrent programs like microservices. 



# **_Rust_**

Rust is best for systems programming. It is versatile and can be used for general purpose programming. When your project demands high performance and scale, Rust is a great choice because of its high execution speed with complex abstraction capability and concurrency and memory safety. 

### Who will appreciate Rust: 

  *     * folks who like C/C++ for speed of execution. 
    * Programmers want complete control of hardware. 
    * Safety again null pointers and data races. 
    * Predictable run times. 



Julia, Go and Rust are very young right now but will challenge python's dominion as python once did to its predecessors. With the benefits of the challengers, it will be hard for python to compete in the future when they are more popular and more libraries are created and maintained. Who knows how long that will take, but it will inevitably happen. One open question is whether industry will adopt these challenges and how long it will take. Microsoft has already publicly endorsed Rust with release of training materials to encourage uptake. However, replacing C in most of Microsoft’s infrastructure will be a huge task. Keep in mind that this task could be expedited by deep learning models that can successfully convert code from one programming language to another. All in all, I believe it’s good to stay abreast of the trends and be dangerous enough with any new skills. You don’t need to be an expert but have a play if you can. I tend to shy away from learning new languages because of the intense time commitment and low retention when not regularly reinforced. But I believe that any time invested now will pay dividends in the future. Also, It is more difficult to monitor the progress and trends in 3 programming languages compared to 1. I really wonder whether Julia, go and rust will specialize further in their strengths. In the meanwhile, I still love python and it’s not going away right now.

# **_Julia, Go & Rust Resources _**

Here are some resources for learning to code in Julia, Go and Rust if you are interested in giving them a try. 

## **General**

See the [programming Idioms website for comparing various control structures like for loops](<https://programming-idioms.org/idiom/223/for-else-loop/3851/python>) in various languages. If you are more familiar with Python or any other programming language, this site may help with mental mapping to Julia, Go or Rust syntax. 

## **Julia**

  *     * [Getting started with Julia](<https://julialang.org/learning/>)
    * [Interactive tutorials for Julia](<http://forio.com/labs/julia-studio/tutorials/>)
    * [First steps with Julia (Kaggle)](<https://www.kaggle.com/c/street-view-getting-started-with-julia>)



## **Go**

  *     * [Go tutorials by Bitfield](<https://bitfieldconsulting.com/golang>)
    * [A Tour of Go](<https://tour.golang.org/>)
    * [Go By Example](<https://gobyexample.com/>)
    * [The Go Playground](<https://play.golang.org/>)



## **Rust**

  *     * [A Gentle Introduction to Rust](<https://stevedonovan.github.io/rust-gentle-intro/>)
    * [Rust By Example](<https://doc.rust-lang.org/rust-by-example/>)
    * [The Rust Playground](<https://play.rust-lang.org/>)



Sources: [1](<https://towardsdatascience.com/5-ways-julia-is-better-than-python-334cc66d64ae>), [2](<https://bitfieldconsulting.com/golang/rust-vs-go>), [3](<https://www.infoworld.com/article/3241107/julia-vs-python-which-is-best-for-data-science.html>)
