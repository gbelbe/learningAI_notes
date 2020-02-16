#Jupyter Notebooks

// free tool to work on jupyter notebooks online:
google colab
https://medium.com/deep-learning-turkey/google-colab-free-gpu-tutorial-e113627b9f5d

https://colab.research.google.com/notebooks/welcome.ipynb


------



notebooks are rendered on github

https://nbviewer.jupyter.org/ to share python notebooks


Notebooks are a form of literate programming proposed by Donald Knuth in 1984. With literate programming, the documentation is written as a narrative alongside the code instead of sitting off by its own. In Donald Knuth's words,

Instead of imagining that our main task is to instruct a computer what to do, let us concentrate rather on explaining to human beings what we want a computer to do.


Another benefit is that the server can be run anywhere and accessed via the internet. Typically you'll be running the server on your own machine where all your data and notebook files are stored. But, you could also set up a server on a remote machine or cloud instance like Amazon's EC2. Then, you can access the notebooks in your browser from anywhere in the world.

install jupyter notebook via pip or conda

## to start a notebook

jupyter notebook

access http://localhost:8888 (next notebooks on 8889...)


# notebooks environments

==> conda install nb_conda

helps manage environments from conda env
(tab on the notebook with conda envs)
you can manage conda env from within notebook: install packages, create new envs..., export envs...

you can access any of your conda env when choosing a kernel (new=> notebook=> select listed envs)

# notebook cell formating

on the top menu par, you can change the formating of the cell to markdown, or code...

# command palette (keyboard icon)

search for menu feature: ex: type **merge** will show command to merge cells&


## Markdown
[markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

links:
[links name](http://url_of_link)
*italics*
**bold**
`inline code`

```
code block
python code
```

Markdown cells using LaTeX symbols. Notebooks use MathJax to render the LaTeX symbols as math symbols. 
$$
y = \frac{a}{b+c}
$$

## Shortcuts

**list of the shortcuts: press "h"**

edit mode / command mode

==> entrée: go into edit mode
==> escape: go back into command mode

==> enter + shift to go to the next cell

==> create a cell above (au dessus) : press "a" letter, or "b" letter to create a cell below

==> do delete a cell press twice "d" (like dd)

==> switch from markdown to code formatting ing a cell: "y" (code) or "m" for markdown

==> activate line numbers: press "l" in command mode

==> save notebook : press "s"


## Magic keywords

magic keywords works for a line or a cell
%matplotlib enable using this in a line
%%timeit in a cell

%pdb ==> activate debug in cells


You can check which version of NumPy you have by typing 
!conda list numpy in your Jupyter Notebook

