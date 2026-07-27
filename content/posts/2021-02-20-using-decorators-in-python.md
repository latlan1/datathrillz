---
title: "Using Decorators in Python"
date: 2021-02-20T17:07:51Z
tags: [code readability, decorators, SWE, timing functions]
categories: [data science, Software Engineering]
draft: false
---

In Python, decorators allow Data Scientists to extend and modify callables, such as functions, methods and classes, without explicitly changing the callable. Using decorators can improve the readability of your code as well code flexibility and modularity. In this article, we’ll discuss why we would use decorators, how to implement decorators and give a few examples.

# **Use Cases for Decorators in Python**

Decorators are powerful because they enable “wrapping” of functions with a master function. Some common use cases for decorators in Python include:

  * Flask uses them to mark and configure the routes
  * Pytest uses them to add marks to the tests
  * Logging calls with parameters
  * Timing calls
  * Access control & authentication (e.g. in Django or other web frameworks where login is required)
  * Memoization (caching)
  * Retry
  * Rate-limiting
  * Function timeout
  * Locking for thread safety

This means that Python developers can change multiple functions at once without explicitly modifying every single function. Let’s say you have 20+ functions in your data science repo and you now need to log all steps taken to train and test your ML model. You could manually copy and paste logging calls to all functions or … you could write a decorator in a few lines and add it to all of your functions. Using decorators will be faster and allow for better maintenance of modular, extendible code in the event that you need to add new functions that also require logging. classmethod() and staticmethod() are common decorators that you may have encountered. 

# **Recipe of a Python Decorator**
[code] 
    def example_decorator(func):
    
        def wrapper(*args, **kwargs):
    
    # do things before the function call e.g. initialize variables
    
    result = func(*args, **kwargs)
    
    # do things with the result of the function, func
    
         return modified_result
    
        return wrapper
[/code]

The example_decorator above accepts a function named func. Decorators must have a callable input and return a callable. The wrapper function can optionally accept other positional and keyword arguments. 

# **Calling Decorators: @mydecorator = mydecorator(function())**

Consider the following example below to illustrate creating and using a decorator:
[code] 
    def strong(func):
    
        def wrapper():
    
            return '<strong>' + func() + '</strong>'
    
        return wrapper
    
    def emphasis(func):
    
        def wrapper():
    
            return '<em>' + func() + '</em>'
    
        return wrapper
[/code]

Above are two decorators called strong and emphasis respectively. To call the decorators, you add @strong or @emphasis immediately before the function that you want to decorate.
[code] 
    @strong
    
    def greet():
    
        return 'Hello!'
[/code]

Now, when you call greet(), you get: 
[code] 
    '<strong>'Hello!'<strong>'
[/code]

This is the same as calling strong(greet()). Essentially, the greet function is overwritten as strong(greet()). Now, you can also stack decorators like so:
[code] 
    @emphasis
    
    @strong
    
    def greet():
    
        return 'Hello!'
[/code]

This returns the equivalent of a chain of callables emphasis(strong(greet())) or:
[code] 
    '<em><strong>'Hello!'<strong><em>'
[/code]

Next, we will present three practical examples of decorators that you can use today. The first is for tracing function calls, the second is for timing function calls and the third is for debugging large codebases. 

# **Decorator Example #1: Trace**

The implementation of a trace decorator (shown below) will indicate when a function is called along with its input arguments and output.
[code] 
    import functools
    
    def trace(func):
    
        @functools.wraps(func)  # pulls the documentation metadata from the function we are wrapping (func)
    
        def wrapper(*args, **kwargs):
    
            print(f'TRACE: calling {func.__name__}() '
    
                  f'with {args}, {kwargs}')
    
            original_result = func(*args, **kwargs)
    
            print(f'TRACE: {func.__name__}() '
    
                  f'returned {original_result!r}')
    
            return original_result
    
        return wrapper
[/code]

By running the code:
[code] 
    @trace
    
    def greet():
    
        ''' This function prints the greeting Hello!'''
        return 'Hello!'
    
    greet()
[/code]

The trace decorator returns the name, arguments and output of the decorated function, which can be immensely helpful with understanding large codebases that call small convenience functions written by someone else and/or that are not directly called.  We use the wraps method from the functools module to ensure that the decorated function carries forward the original function’s doc string info and name when called. This means that when you call help(greet) on the decorated function, you get the greet docstring, which may be helpful for debugging other, more complex decorated functions.

# **Decorator Example #2: Timing**

Another popular use of decorators is for the ease of timing functions in your code.
[code] 
    import functools
    
    import time
    
    def timer(func):
    
        """Print the runtime of the decorated function"""
    
        @functools.wraps(func)
    
        def wrapper_timer(*args, **kwargs):
    
            start_time = time.perf_counter()    # 1
    
            value = func(*args, **kwargs)
    
            end_time = time.perf_counter()      # 2
    
            run_time = end_time - start_time    # 3
    
            print(f"Finished {func.__name__!r} in {run_time:.4f} secs")
    
            return value
    
        return wrapper_timer
    
    @timer
    
    def waste_some_time(num_times):
    
        for _ in range(num_times):
    
            sum([i**2 for i in range(10000)])
[/code]

The timer decorator starts the timer before the function is called, calls the function then stops the timer. It then prints the time taken for the function call. 
[code] 
    >>> waste_some_time(1)
    
    Finished 'waste_some_time' in 0.0010 secs
    
    >>> waste_some_time(999)
    
    Finished 'waste_some_time' in 0.3260 secs
[/code]

You can add the timer decorator to any function that you want to time - it’s fast and easy.

# **Decorator Example #3: Debug**

This example is similar to example #1 but allows you to add log statements to called functions, which can help with debugging problems with your code. Collaborators on your code will thank you for the ability to quickly trace any bugs down to the problem function. 
[code] 
    import functools
    
    import logging
    
    logger = logging.getLogger(__name__)
    
    def debug(level): 
    
        def mydecorator(f)
    
            @functools.wraps(f)
    
            def log_f_as_called(*args, **kwargs):
    
                logger.log(level, f'{f} was called with arguments={args} and kwargs={kwargs}')
    
                value = f(*args, **kwargs)
    
                logger.log(level, f'{f} return value {value}')
    
                return value
    
            return log_f_as_called
    
        return mydecorator
    
    @debug(level='info')
    
    def hello():
    
        print('hello')
[/code]

The debug decorator accepts an argument that indicates the log level (info, warning, or error, etc.), which can be defined for each function that it decorates.

## **Example of logging decorator using partial function**
[code] 
    import functools
    
    def debug(f=None, *, level='debug'): 
    
        if f is None:
    
            return functools.partial(debug, level=level)
    
        @functools.wraps(f)   # we tell wraps that the function we are wrapping is f
    
        def log_f_as_called(*args, **kwargs):
    
            logger.log(level, f'{f} was called with arguments={args} and kwargs={kwargs}')
    
            value = f(*args, **kwargs)
    
            logger.log(level, f'{f} return value {value}')
    
            return value
    
        return log_f_as_called
[/code]

The partial function, f , is used to wrap the debug function with the specified argument level such that a partially filled out function is returned. Now, you can call the decorator with default logging level set to ‘debug’ (just as before but with a partial function that is slightly more elegant) :
[code] 
    @debug
    
    def hello():
    
        print('hello')
[/code]

Or you can use the debug decorator by overriding the default log level:
[code] 
    @debug('warning')
    
    def hello():
    
        print('hello')
[/code]

In conclusion, decorators are Python functions that wrap other functions. You can see more examples at the [Python Decorator Library](<https://wiki.python.org/moin/PythonDecoratorLibrary>) and the [Python Decorator Wiki](<https://wiki.python.org/moin/PythonDecorators>).  This article has discussed what decorators are, how they are used and how to implement them with several practical examples. Callables such as functions can be decorated many times. The use of decorators is indicative of an seasoned Python developer - start upp’ing your Python coding level today by using decorators! Sources: [1](<https://dbader.org/blog/python-decorators>), [2](<https://code-maven.com/slides/python/decorator-use-cases>), [3](<https://timber.io/blog/decorators-in-python/>), [4](<https://realpython.com/primer-on-python-decorators/>)
