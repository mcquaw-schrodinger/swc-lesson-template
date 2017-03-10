---
title: "Built-in Functions & Magic Commands"
teaching: 15
exercises: 0
questions:
- 
keypoints:
- 
---
# Making Your Jupyter Notebook Magical
If you want to get the most out of your notebooks with the IPython kernel, you should consider learning about the so-called "magic commands". Also, consider adding even more interactivity to your notebook so that it becomes an interactive dashboard to others should be one of your considerations! 

## The Notebook's Built-In Commands
There are some predefined ‘magic functions’ that will make your work a lot more interactive.

To see which magic commands you have available in your interpreter, you can simply run the following:

    %lsmagic

Tip: the regular Python help() function also still works and you can use the magic command %quickref to show a quick reference sheet for IPython.

And you'll see a whole bunch of them appearing. You'll probably see some magics commands that you'll grasp, such as %save, %clear or %debug, but others will be less straightforward.

If you're looking for more information on the magics commands or on functions, you can always use the ?, just like this:

    # Retrieving documentation on the alias_magic command
    ?%alias_magic

    # Retrieving information on the range() function
    ?range
Note that if you want to start a single-line expression to run with the magics command, you can do this by using % . For multi-line expressions, use && . The following example illustrates the difference between the two:

    %time x = range(100)
    %%timeit x = range(100)
        max(x)
Stated differently, the magic commands are either line-oriented or cell-oriented. In the first case, the commands are prefixed with the % character and they work as follows: they get as an argument the rest of the line. When you want to pass not only the line but also the lines that follow, you need cell-oriented magic: then, the commands need to be prefixed with %%.

Besides the %time and %timeit magics, there are some other magic commands that will surely come in handy:

<table>
<tr><td>%pdb</td><td>Debug</td></tr>
<tr><td>%prun</td><td>Do a performance run</td></tr>
<tr><td>%writefile</td><td>Saves the contents of a cell to an external file</td></tr>
<tr><td>%pycat</td><td>Shows the syntax highlighted contents of an external file</td></tr>
<tr><td>%who</td><td>List all variables of a global scope</td></tr>
<tr><td>%store</td><td>Pass variables between notebooks</td></tr>
<tr><td>%load</td><td>Insert code from an external script</td></tr>
<tr><td>%run</td><td>Execute Python code</td></tr>
<tr><td>%env</td><td>Set environment variables</td></tr>
</table>

Note that this is just a short list of the handy magic commands out there. There are many more that you can discover with %lsmagic.

You can also use magics to mix languages in your notebook with the IPython kernel without setting up extra kernels: there is rmagics to run R code, SQL for RDBMS or Relational Database Management System access and cythonmagic for interactive work with cython,... But there is so much more! 

To make use of these magics, you first have to install the necessary packages:

    pip install ipython-sql
    pip install cython
    pip install rpy2

Tip: if you want to install packages, you can also execute these commands as shell commands from inside your notebook by placing a ! in front of the commands, just like this:

    # Check, manage and install packages
    !pip list
    !pip install ipython-sql

    # Check the files in your working directory
    !ls
Only then, after a successful install, can you load in the magics and start using them:

    %load_ext sql
    %load_ext cython
    %load_ext rpy2.ipython
Let's demonstrate how the magics exactly work with a small example:

    # Hide warnings if there are any
    import warnings
    warnings.filterwarnings('ignore')

    # Load in the r magic
    %load_ext rpy2.ipython

    # We need ggplot2
    %R require(ggplot2)

    # Load in the pandas library
    import pandas as pd

    # Make a pandas DataFrame
    df = pd.DataFrame({'Alphabet': ['a', 'b', 'c', 'd','e', 'f', 'g', 'h','i'],
                       'A': [4, 3, 5, 2, 1, 7, 7, 5, 9],
                       'B': [0, 4, 3, 6, 7, 10, 11, 9, 13],
                       'C': [1, 2, 3, 1, 2, 3, 1, 2, 3]})

    # Take the name of input variable df and assign it to an R variable of the same name
    %%R -i df

    # Plot the DataFrame df
    ggplot(data=df) + geom_point(aes(x=A, y=B, color=C))
This is just an initial not nearly everything you can do with R magics, though. You can also push variables from Python to R and pull them again to Python. Read up on the documentation (with easily accessible examples!) here.
