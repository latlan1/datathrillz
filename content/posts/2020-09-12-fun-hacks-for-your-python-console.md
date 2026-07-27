---
title: "Fun Hacks for your Python Console"
date: 2020-09-12T12:37:09Z
categories: [python hacks]
draft: false
---

## Hack #1: Color Text in Your Terminal 

You can change the colors of text shown in your Python terminal console using ANSI escape character sequences! Or you can use the [colorama](<https://pypi.org/project/colorama/>) library to make the process a bit easier and more streamlined. Colorama works across all the platforms i.e. Windows, Mac OS and Unix. 

First, we import the modules that we need from colorama.
[code] 
    from colorama import Fore, Back, Style 
[/code]

Next, we can specify the foreground and background colors of any text. We can combine the effects by using a plus sign with the Fore, Back and/or Style modules.

![](/images/colorama_examples.png)

Here are all of the options for foreground and background colors and styles of text printed to the console. 
[code] 
    Fore: BLACK, RED, GREEN, YELLOW, BLUE, MAGENTA, CYAN, WHITE, RESET.
    Back: BLACK, RED, GREEN, YELLOW, BLUE, MAGENTA, CYAN, WHITE, RESET.
    Style: DIM, NORMAL, BRIGHT, RESET_ALL
[/code]

Alternatively, we could use the cprint function from the termcolor library to print colored text. The syntax is a bit easier to use.

![](/images/termcolor_cprint_magenta_on_cyan.png)

## Hack #2: Format Text in Your Terminal

The Pyfiglet package renders ASCII text in various ASCII art fonts and colors. This is a nice way to spruce up any text that you need to output to the console e.g. to indicate the start of a scientific computation pipeline. 

Here are some examples:

![](/images/pyfiglet_magenta_1.png)

![](/images/pyfiglet_blue_2.png)

![](/images/pyfiglet_magenta_3.png)

You can check out more Pyfiglet [fonts ](<https://github.com/pwaller/pyfiglet/tree/master/pyfiglet/fonts>)and [examples](<https://www.geeksforgeeks.org/python-ascii-art-using-pyfiglet-module/>).
