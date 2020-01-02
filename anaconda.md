 #Anaconda, package manager and library installer for big data:

conda = package manager + environment management (like virtualenv)


## create new environment in python

conda create -n project_name python=3

## to activate the env, type:

source activate env_name
or conda activate env_name


## to list all created environments
conda env list


## to leave an environment
source deactivate
or conda deactivate

## to remove an env:
conda env remove -n env_name


## install other packages like

conda install numpy pandas matplotlib
conda install jupyter notebook
conda list


## Export environment installed packages to a text file to be able to share your env with others

==> conda env export > environment.txt
==> conda env export > environment.yml

to create an env from a text file:

==> conda env create -f environment.txt (or .yml)
or
==> conda create --name MyEnvironment --file environment.txt 


same thing works with pip
==> pip freeze > requirements.txt

## conda upgrade conda
conda upgrade conda
conda upgrade --all

conda update --all
conda list
conda search '*searchtext*'


==> note sharing environment can be useful for github projects, can use also pip freeze for people not using conda
