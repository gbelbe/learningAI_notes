
# input('enter a name: ')  ==> prompt a user to enter a name

note input function collects input as a string.
Needs to add int or float if we want to use it as a number


# two types of errors:

syntax_errors (badly formated python code)

exception_errors ==> when unexpected things happens to our code
    value_error ==> inapropriate value for the expected type


# Handling exception, helps to avoid program to crash when it enconter an exception:

python tries to run the code in the try block, if it fails with an error, it goes to the except block
but it continues to run even if it goes to the except block, so the last print statement will run even if the error has occured


try:
    int(input("enter a valid number")

except:
    print('that\'s not a valid number')

print("good result")


## if we want to force the code not to run if it goes through an error:

while True:
    try:
        int(input("enter a valid number")
        break
    except:
        print('not valid number, try again')
    finally:
        print("input entered")

break will pass the loop if the previous item is run with success (no error happens)

finally: will run this code whatever happens

we can also specify which error to handle, like **except ValueError:**




## working with files

1st, open file:
f = open('/my_path/my_file.txt', 'r')  ==> python object to which python interacts with the file, in mode 'r' read only
file_data = f.read()
f.close()  ==> frees up system resources used to read the file

to write on a file: 'w', but it will delete whatever is inside. or 'a' to append at the end of the file


with open('/my_file.txt', 'r') as f:
    file_data = f.read()

using "with -- as" enables to work on a file inside a block, when the block is left, the file is automatically closed, but you can access to file_data

f.read(5)  ==> reads up to the 5th char and keep the window at this char.
f.read(8)  ==> reads from 6 to 6+8 char
f.read()   ==> reads until the end

read the next line in a file: f.readlines(), or

lines_list = []
with open("camelot.txt") as f:
    for line in f:
        lines_list.append(line.strip())

print(lines_list) 




## Importing libraries:

import file_name_without_dot_py
or import file_name as f

qand on importe un fichier avec import, python crée un object avec le nom du fichier importer.
Pour lire une méthode ou une variable de ce fichier == Module, on appelle ce nom suivi d'un point.

import useful_functions

useful_functions.mean(scores)


If we want a script to be imported as a module but not all of it to be fully executed when imported.
i.e. run the script will run tests.

if __name__ == '__main__':  (if name of the file == main program being run)
    bloc of code to be executed only when the main program being run is equal to this file name. (not run when it is imported inside another file)

generally we place all the executable statements inside this if __name__ bloc.



# Our favourite modules

The Python Standard Library has a lot of modules! To help you get familiar with what's available, here are a selection of our favourite Python Standard Library modules and why we use them!

    csv: very convenient for reading and writing csv files
    collections: useful extensions of the usual data types including OrderedDict, defaultdict and namedtuple
    random: generates pseudo-random numbers, shuffles sequences randomly and chooses random items
    string: more functions on strings. 
        This module also contains useful collections of letters like string.digits (a string containing all characters which are valid digits).
    re: pattern-matching in strings via regular expressions
    math: some standard mathematical functions
    os: interacting with operating systems
    os.path: submodule of os for manipulating path names
    sys: work directly with the Python interpreter
    json: good for reading and writing json files (good for web work)

import only some methods from a module (to make it lighter)

from collections import defaultdict, namedtuple ==> then you use the method directly without calling the module.

or from collections import defaultdict as defdict

# package: module that contains submodules

ex: import os.path will import the submodule path within the module os

# pip standard package manager for python

or Anaconda for data science

use pip install library first

import in your script just as std libraries, but standard to import after standard libraries imports

pip install ipython (new python interpretor)
ipython
python interpreter with autocomplte (tab, information about objects ?, ! execute shell commands

# use requirements.txt to list all libraries

requirements.txt

pytz==2016.7
requests==2.11.1
...
names and version number

## pip install project dependancies:

pip install -r requirements.txt

## argparse: create nice artuments command lines

## Immutable data types: int, string...

## Mutable data type: list, set, dict

list scope  extended to a funciton if :
a mutable data type created outside a function can be passed to a function through its arguments.
it will be possible to modify it from within the function

list scope limited to the function is list is created in the function and not returned
