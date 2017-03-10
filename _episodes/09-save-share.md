# Share Your Jupyter Notebooks
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

# Jupyter Notebooks in Practice
This all is very interesting when you're working alone on a data science project. But most times, you're not alone. You might have some friends look at your code or you'll need your colleagues to contribute to your notebook.

How should you actually use these notebooks in practice when you're working in a team?

The following tips will help you to effectively and efficiently use notebooks on your data science project.

# Tips To Effectively and Efficiently Use Your Jupyter Notebooks
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

# Jupyter Notebooks for Data Science Teams: Best Practices
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
