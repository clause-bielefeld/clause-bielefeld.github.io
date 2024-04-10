---
layout: post
title: Getting started with Python and Anaconda
permalink: teaching/python/
---


We mainly rely on Python as a programming language for both research and teaching.
This page is intended to provide a (brief) overview of how to install Python, and some ways to write and run Python code.

On this page you can find information on:
1. Installing Python via the Anaconda distribution
2. Different ways to use Python (interactive mode, scripts, notebooks)
3. Using Python via the command line on Windows

## 1. Installing Python via the Anaconda distribution

Whereas Python is usually preinstalled on Linux distributions such as Ubuntu or Mint, this is not necessarily the case with all operating systems.
There are different ways to install Python. To our students we recommend [Anaconda](https://www.anaconda.com/products/individual), which is briefly described below.

### Overview

The Anaconda distribution contains Python as well as a number of additional tools, such as:
  - **Jupyter Notebook / Jupyter Lab** - allows for writing and running Python code in a browser-based environment. In .ipynb notebooks, input code, outputs, visualizations / plots and further markdown descriptions are combined within a single file.
  - **Qt Console** - an interactive interpreter, which supports features such as syntax highlighting and displaying plots
  - **conda** - a package manager, which can be used to set up separate Python environments, each condaining each own Python version and additional modules
  - **Anaconda Navigator** - a graphical interface for accessing Anaconda applications (such as Jupyter Notebook / Lab) as well as managing conda environments.

Apart from that, Anaconda comes with a large number of pre-installed Python packages, including the majority of modules that we use in our courses and lectures. You can find comprehensive instructions on how to use Anaconda in the [official documentation](https://docs.anaconda.com/anaconda/).

We recommend Anaconda to students who have little or no background in programming. More experienced students can also take a look at [Miniconda](https://docs.conda.io/en/latest/miniconda.html), which requires less disk space but involves slightly more effort to set up.

### Installation

The Anaconda Individual Edition can be downloaded [here](https://www.anaconda.com/products/individual). The Anaconda Documentation includes [detailed instructions](https://docs.anaconda.com/anaconda/install/) for installing and setting up Anaconda on Windows, macOS or Linux.

### Accessing Tools

There are two ways of accessing the tools which are included in the Anaconda distribution: Via the Anaconda Navigator or directly using the command line.

**Anaconda Navigator** is a graphical user interface (GUI) which can be used to access applications such as Jupyter Lab or the Qt Console, as well as for managing conda environments. On Linux machines you can start Anaconda Navigator by executing ``anaconda-navigator`` in the command line. On Windows, you can find it in your start menu (e.g. by hitting the windows button and typing "Anaconda Navigator").

Using the **command line**, many Anaconda applications can be accessed more directly and in the desired directory. For example, in Linux you can run ``jupyter-lab`` and ``jupyter notebook`` to run Jupyter Lab and Jupyter Notebook, respectively. To use Anaconda from the command line, it must be **initialized** in the command line interface. To see if this is the case, start a Terminal (Linux / Mac) or Powershell (Windows) session. If conda is initialized, the command prompt will be preceded by ``(base)``, i.e. you will see ``(base) user@host:~$``. This indicates that (a) conda is initialized and (b) you are currently in the default *base* environment (see next section). 
When installing Anaconda, you will be asked if conda should be initialized by default. If ``(base)`` is missing, you can try running the command ``conda init`` (and then restarting the terminal), or (on Windows) using the *Anaconda Prompt* (from the Start menu) instead of Powershell.

### Managing Environments and Installing Modules

 Anaconda includes **conda**, a package manager that can be used to set up separate Python environments, each containing its own version of Python and additional modules. Although managing environments with conda is not necessary for beginners who mainly rely on pre-installed modules from the [Python Standard Library](https://docs.python.org/3/library/index.html), it is **highly recommended** for larger projects with more dependencies.

 To manage conda environments from the command line, make sure *conda* is initialized (as indicated by the ``(base)`` prefix, see previous section). ``(base)`` indicates that you are currently in the default *base* environment. 

 **Additional environments** (e.g. for new projects) can be created using the command ``conda create --name myenv``, where ``myenv`` can be replaced with any name for your environment. (Note that it is also possible to create environments with specific Python versions, e.g. ``conda create --name myenv python=3.8``. To delete environments, run ``conda remove --name myenv --all``.) Once created, you can switch to the new environment with ``conda activate myenv`` (where ``myenv`` is replaced with the respective environment name).

 With the environment enabled, you can now start **installing additional Python packages / modules**. This can be done through *conda* itself, e.g. using the command ``conda install numpy`` to install NumPy. (The actual commands can be easily found via Google, e.g. searching for "conda install nltk" will take you to a subpage of [https://anaconda.org](https://anaconda.org) where you can find a command to copy&paste). Alternatively, you can use *pip* to install new packages. To do this, you must first install pip itself (with ``conda install pip``). Then you can install e.g. NumPy with ``pip install numpy``. (Again, Google will lead you to the commands for the packages you want to install).
 Using either *conda* or *pip* should work in most cases, but sometimes packages on *pip* are more up-to-date.

 Conda environments can also be **accessed in Jupyter Notebook/Lab**. This requires two additional steps: First, in the activated environment, run ``conda install -c anaconda ipykernel`` (or ``pip install ipykernel`` if you are using *pip*), followed by ``python -m ipykernel install --user --name=myenv`` (replacing ``myenv`` with the name of the environment). After this (and restarting any running sessions) you should be able to select the environment in Notebook/Lab. (More detailed instructions can be found [here](https://medium.com/@nrk25693/how-to-add-your-conda-environment-to-your-jupyter-notebook-in-just-4-steps-abeab8b8d084).)

 Further information on conda environments (and instructions for how to manage environments in the Anaconda Navigator) can be found [here](https://conda.io/projects/conda/en/latest/user-guide/index.html).

## 2. Getting started with Python

After installing Python, you can write and run code in three different ways: Via the **interactive interpreter**, by writing and executing **Python scripts** (file extension: .py), and in **Jupyter/IPython notebooks** (file extension: .ipynb).

### Interactive Interpreter

Python can be used in an "interactive mode". Here, individual commands are executed directly and the results are returned to the user in command line style. The interactive mode can be started in Anaconda by the tool "Qt Console" or via the command line (e.g. by typing in ``python`` in Linux).

Python's interactive mode can be used for trying out individual commands (something like ``print(2+3)``) or becoming familiar with the basic syntax in Python. However, it is not suitable for general programming work for different reasons. For example, the interactive mode is not built to store code permanently.

### Python Scripts

Writing Python scripts can be considered the canonical way to program with Python.

The general flow is as follows: Using a text editor, the Python code is written to a text file, which is saved with the .py file extension. This file is passed to the Python interpreter (for example, by executing the command ``python filename.py`` in Linux). The code in the file is now executed line by line, from top to bottom, and print statements are displayed in the command line.

Some good editors are e.g. [Visual Studio Code](https://code.visualstudio.com/), [Sublime Text](https://www.sublimetext.com/) or [Vim](https://www.vim.org/) (for more advanced users). If you only have to write a few lines, you might as well use any preinstalled text editor, such as Notepad on Windows.

Note: The Anaconda distribution includes Spyder; an integrated development environment (IDE) for working with .py files. In Spyder, scripts can be created, edited and executed without switching between the editor and the command line. While all of this can be useful, many functions are not needed for beginners and may be distracting. Also, knowing how to use the command line is a skill that is helpful in many cases and indispensable in others. Therefore, we strongly recommend that students become familiar with the command line *at least* to the point where they can navigate between folders and run Python scripts.

### Notebooks

Jupyter Notebooks are documents, which can contain Python code, interpreter outputs, plots, visualizations and other kind of text (i.e. plain text or [Markdown](https://en.wikipedia.org/wiki/Markdown) in a single file. Notebooks can be created, edited and run in a browser-based environment, using the Anaconda applications Notebook or JupyterLab.

In notebooks, code and text can be clustered in individuall "cells". You can think of code cells as individual Python scripts: They can be run independently, the output is displayed below the respective code cell. Cells can be run in any order - e.g. all cells from top to bottom, individual cells in any order, or the same cells multiple times. If a code cell is run, it can access everything which was set by previous cells - for example variables, which have been defined, or imported modules.

Notebooks can be created or accessed through the browser-based Jupyter Notebook/Lab environments. Alternatively, editors such as Visual Studio Code provide plug-ins for working with notebooks.

A more detailed description of what notebooks can do and how to use them can be found in the [JupyterLab documentation](https://jupyterlab.readthedocs.io/en/stable/user/notebook.html).

## 3. Using Python via the command line on Windows

On Windows, Python can be used from the [command line](https://en.wikipedia.org/wiki/Command-line_interface) just like in Linux or MacOS. For this, the file *python.exe*, which is created when installing Anaconda, has to be run from a command line interpreter. However, some setup steps might be necessary, which are described below.

"Windows PowerShell" is the pre-installed command line interpreter on Windows. (Alternatively, you can use the Anaconda Prompt.) PowerShell can be started either from the start menu, or from the Windows Explorer in any directory (via "File" -> "Open Windows PowerShell"). After starting PowerShell, a so-called [command prompt](https://en.wikipedia.org/wiki/Command-line_interface#Command_prompt) is displayed, which indicates that PowerShell is ready to accept commands. In PowerShell the prompt consists of "PS", followed by the [path](https://en.wikipedia.org/wiki/Path_(computing)) to the current directory and a subsequent ">". If PowerShell is run from Explorer, it directly starts in the directory which was opened in the Explorer.

To run the **Python interpreter in interactive mode**, the full (*absolute*) path to python.exe can be entered in PowerShell.
For example: `C:\Users\YourName\anaconda3\python.exe`. This path will look different, depending on the directory where Anaconda was installed. Hint: Use the "Tab" key to auto-complete commands or paths while entering them in PowerShell; use the up and down arrow keys to toggle between commands recently executed.

To run a **Python script** in the command line, first enter the path to python.exe (as shown before), and then a second path to the .py file which is supposed to be run. For example:
`C:\Users\YourName\anaconda3\python.exe C:\Users\YourName\Documents\test.py`.

As a more compact alternative to absolute paths, *relative* paths can be used. You can think of relative paths as the way to a file or folder, which has to be taken from the directory PowerShell is currently in. For example, a Python script in the same directory can be executed as follows:
`C:\Users\YourName\anaconda3\python.exe .\test.py` (the ".\" in front of "test.py" stands for "this directory").

Finally, calling the Python interpreter itself (the python.exe) can be simplified significantly. If the environment variable *PATH* contains the path to the directory where python.exe is located in, the Python interpreter can be run in PowerShell as easy as using the command `python` (instead of the absolute or relative path to python.exe). In some cases this is done automatically when installing Anaconda. If the interpreter does not start if `python` is run, you can follow the steps below to add the Python directory to the *PATH* variable:

1. in the Explorer (where you can see folders and files), go to the directory where python.exe was installed
2. right click at the address bar on the top of the Explorer window and copy the address (e.g. `C:\Users\YourName\anaconda3`, **without** the file name "python.exe")
3. right click on "Computer" on the left side, click on "Settings"
4. click on "Advanced System Settings" (on the right)
5. click on "Environment variables"
6. select variable "Path" (or "PATH") in "User variables" and click on "Edit"
7. click on "New" and paste the address that was copied in step 2
8. press Enter and move the added path to the top
9. confirm

If those steps are successful, the Python interpreter can be started in interactive mode by using the PowerShell command `python`.
A Python script in the same folder can be run using the command `python .\test.py` (where "test.py" must be replaced by the respective name of the script).

[Here](https://docs.python.org/3/using/index.html) you can find detailed information about setting up Python on different operation systems; including [more detailed instructions for Windows](https://docs.python.org/3/using/windows.html).





<br/><br/>
