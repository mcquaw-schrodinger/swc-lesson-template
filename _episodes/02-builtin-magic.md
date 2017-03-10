---
title: "Built-in Functions & Magic Commands"
teaching: 15
exercises: 0
questions:
- 
keypoints:
- 
---
Making Your Jupyter Notebook Magical
If you want to get the most out of your notebooks with the IPython kernel, you should consider learning about the so-called "magic commands". Also, consider adding even more interactivity to your notebook so that it becomes an interactive dashboard to others should be one of your considerations! 

The Notebook's Built-In Commands

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

%pdb	Debug
%prun	Do a performance run
%writefile	Saves the contents of a cell to an external file
%pycat	Shows the syntax highlighted contents of an external file
%who	List all variables of a global scope
%store	Pass variables between notebooks
%load	Insert code from an external script
%run	Execute Python code
%env	Set environment variables
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

Interactive Notebooks As Dashboards: Widgets

The magic commands already do a lot to make your workflow with notebooks agreeable, but you can also take additional steps to make your notebook an interactive place for others by adding widgets to it!

To add widgets to your notebook, you need to import widgets from ipywidgets:

from ipywidgets import widgets
That's enough to get started! You might want to think now of what type of widget you want to add. The basic types of widgets are text input, buttons, and input-based widgets.  

See an example of a text input widget below:
<img alt="Interactive Jupyter Notebook Widgets" src="http://community.datacamp.com.s3.amazonaws.com/community/production/ckeditor_assets/pictures/201/content_jupyternotebook6b.gif">
This example was taken from a wonderful tutorial on building interactive dashboards in Jupyter, which you can find on this page.

Share Your Jupyter Notebooks
In practice, you might want to share your notebooks with colleagues or friends to show them what you have been up to or as a data science portfolio for future employers. However, the notebook documents are JSON documents that contain text, source code, rich media output, and metadata. Each segment of the document is stored in a cell.

Ideally, you don't want to go around and share JSON files. 

That's why you want to find and use other ways to share your notebook documents with others.

When you create a notebook, you will see a button in the menu bar that says "File". When you click this, you see that Jupyter gives you the option to download your notebook as an HTML, PDF, Markdown or reStructuredText, or a Python script or a Notebook file.

You can use the nbconvert command to convert your notebook document file to another static format, such as HTML, PDF, LaTex, Markdown, reStructuredText, ... But don't forget to import nbconvert first if you don't have it yet! 

Then, you can give in something like the following command to convert your notebooks: 

jupyter nbconvert --to html Untitled4.ipynb
With nbconvert, you can make sure that you can calculate an entire notebook non-interactively, saving it in place or to a variety of other formats. The fact that you can do this makes notebooks a powerful tool for ETL and for reporting. For reporting, you just make sure to schedule a run of the notebook every so many days, weeks or months; For an ETL pipeline, you can make use of the magic commands in your notebook in combination with some type of scheduling.

Besides these options, you could also consider the following:

You can create, list and load GitHub Gists from your notebook documents. You can find more information here. Gists are a way to share your work because you can share single files, parts of files, or full applications.
With jupyterhub, you can spawn, manage, and proxy multiple instances of the single-user Jupyter notebook server. In other words, it's a platform for hosting notebooks on a server with multiple users. That makes it the ideal resource to provide notebooks to a class of students, a corporate data science group, or a scientific research group.
Make use of binder and tmpnb to get temporary environments to reproduce your notebook execution. 
You can use nbviewer to render notebooks as static web pages. 
To turn your notebooks into slideshows, you can turn to nbpresent and RISE.
jupyter_dashboards will come in handy if you want to display notebooks as interactive dashboards.
Create a blog from your notebook with Pelican plugin.
Jupyter Notebooks in Practice
This all is very interesting when you're working alone on a data science project. But most times, you're not alone. You might have some friends look at your code or you'll need your colleagues to contribute to your notebook.

How should you actually use these notebooks in practice when you're working in a team?

The following tips will help you to effectively and efficiently use notebooks on your data science project.

Tips To Effectively and Efficiently Use Your Jupyter Notebooks
Using these notebooks doesn't mean that you don't need to follow the coding practices that you would usually apply.

You probably already know the drill, but these principles include the following:

Try to provide comments and documentation to your code. They might be a great help to others!
Also consider a consistent naming scheme, code grouping, limit your line length, ...  
Don't be afraid to refactor when or if necessary
In addition to these general best practices for programming, you could also consider the following tips to make your notebooks the best source for other users to learn:

Don't forget to name your notebook documents!
Try to keep the cells of your notebook simple: don't exceed the width of your cell and make sure that you don't put too many related functions in one cell.  
If possible, import your packages in the first code cell of your notebook, and
Display the graphics inline. The magic command %matplotlib inline will definitely come in handy to suppress the output of the function on a final line. Don't forget to add a semicolon to suppress the output and to just give back the plot itself. 
Sometimes, your notebook can become quite code-heavy or maybe you just want to have a cleaner report. In those cases, you could consider hiding some of this code. You can already hide some of the code by using magic commands such as %run to execute a whole Python script as if it was in a notebook cell. However, this might not help you to the extent that you expect. In such cases, you can always check out this tutorial on optional code visibility or consider toggling your notebook's code cells.
Jupyter Notebooks for Data Science Teams: Best Practices
Jonathan Whitmore wrote in his article some practices for using notebooks for data science and specifically addresses the fact that working with the notebook on data science problems in a team can prove to be quite a  challenge. 

That is why Jonathan suggests some best practices:

Use two types of notebooks for a data science project, namely, a lab notebook and a deliverable notebook. The difference between the two (besides the obvious that you can infer from the names that are given to the notebooks) is the fact that individuals control the lab notebook, while the deliverable notebook is controlled by the whole data science team, 
Use some type of versioning control (Git, Github, ...). Don't forget to commit also the HTML file if your version control system lacks rendering capabilities, and 
Use explicit rules on the naming of your documents.  
Learn From The Best Notebooks
This section is meant to give you a short list with some of the best notebooks that are out there so that you can get started on learning from these examples. 

Notebooks are also used to complement books, such as the Python Data Science Handbook. You can find the notebooks here.
A report on a Kaggle competition is written down in this blog, generated from a notebook.
This matplotlib tutorial is a great example of how well a notebook can serve as a means of teaching other people topics such as scientific Python. 
Lastly, make sure to also check out The Importance of Preprocessing in Data Science and the Machine Learning Pipeline tutorial series that was generated from a notebook.
Note that this list is definitely not exhaustive. There are many more notebooks out there!

You will find that many people regularly compose and have composed lists with interesting notebooks. Don't miss this gallery of interesting IPython notebooks or this KD Nuggets article.