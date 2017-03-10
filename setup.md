---
layout: page
title: "Setup"
permalink: /setup/
---
# Prerequisites
* Schrodinger 2017-1 installed
* Create Schrodinger 2017-1 Python virtualenv
* Install Jupyter package within virtualenv

Please set up your python environment at least a day in advance of the workshop.  If you encounter problems with the installation procedure, ask your workshop organizers via e-mail for assistance so you are ready to go as soon as the workshop begins.

1. Install Schrodinger 2017-1 software suite
Instructions available at [Schrodinger website][schrodinger-install].

1. Create Schrodinger 2017-1 Python virtualenv
Working within a Schrodinger Python virtualenv allows for easy access of Schrodinger Python functionality without disruption of native Python installations and is strongly recommended.  More details regarding Schrodinger Python virtualenv can be found in the [documentation][schrodinger-virtualenv].

    # Confirm your version of SCHRODINGER is 2017-1
    echo $SCHRODINGER

You should see something similar to...

    /opt/schrodinger/suites2017-1

Use the schrodinger_virtualenv.py script to create a local Schrodinger Python virtualenv.

    # Create virtualenv using Schrodinger Python
    $SCHRODINGER/run schrodinger_virtualenv.py sch_v37

    # Activate the new virtualenv
    source sch_v37/bin/activate

You should see something similar to...

    Note: The Schrodinger virtualenv is tied to a specific SCHRODINGER value.
    This virtualenv is tied to SCHRODINGER=/opt/schrodinger/suites2017-1.

    If you change your SCHRODINGER environment variable, it will break the ability
    to use the unadorned python command.

1. Install Jupyter package
Schrodinger 2017-1 comes with most, but not all of the required packages for running a Jupyter Notebook.  Simply use pip to install Jupyter in order to begin using a notebook.

Verify that pip is utilizing your Schrodinger Python packages and install Jupyter.

    # Run Python from commandline and use get_python_lib() to print library directory
    python -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())"

You should see something similar to...

    {directory of virtualenv}sch_v37/lib/python2.7/site-packages

Install the latest version of Jupyter (see the [Jupyter website][jupyter-install] for details).

    # Use pip to install Jupyter 1.* 
    pip install jupyter
    
    # Confirm Jupyter installation
    pip show jupyter
    
You should see something similar to...

    Name: jupyter
    Version: 1.0.0
    Summary: Jupyter metapackage. Install all the Jupyter components in one go.
    Home-page: http://jupyter.org
    Author: Jupyter Development Team
    Author-email: jupyter@googlegroups.org
    License: BSD
    Location: /Users/mcquaw/Virtualenvs/sch_v37/lib/python2.7/site-packages
    Requires: ipykernel, qtconsole, jupyter-console, notebook, nbconvert, ipywidgets

## Getting the Data

FIXME:
The data we will be using is taken from the [gapminder][gapminder] dataset.
To obtain it, download and unzip the file 
[python-novice-gapminder-data.zip]({{page.root}}/files/python-novice-gapminder-data.zip).
In order to follow the presented material, you should launch a Jupyter 
notebook in the root directory (see [Starting Python](#Starting-Python)).
FIXME:

## Starting Python

We will teach Python using the [Jupyter notebook][jupyter], a 
programming environment that runs in a web browser. Jupyter requires a reasonably 
up-to-date browser, preferably a current version of Chrome, Safari, or Firefox 
(note that Internet Explorer version 9 and below are *not* supported).

To start the notebook, open a terminal or git bash and type the command:

~~~
$ jupyter notebook
~~~
{: .bash}

To start the Python interpreter without the notebook, open a terminal 
or Git Bash and type the command:

~~~
$ python
~~~
{: .bash}

[schrodinger]: https://www.schrodinger.com/downloads/releases
[schrodinger-install]: https://www.schrodinger.com/sites/default/files/s3/mkt/Documentation/2017-1/docs/Documentation.htm#install_guide/install_guideTOC.htm
[schrodinger-virtualenv]: http://content.schrodinger.com/Docs/r2017-1/python_api/intro.html#experimental-environments-with-virtualenv
[gapminder]: http://gapminder.org
[jupyter]: http://jupyter.org/
[jupyter-install]: http://jupyter.readthedocs.io/en/latest/install.html#optional-for-experienced-python-developers-installing-jupyter-with-pip
[python]: https://python.org
