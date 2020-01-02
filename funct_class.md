
def funct_name(arg1, arg2=5):
    arg2=5 ==> default value for argument    
    xxx
    return variable

def funct_name():
    print("toto")


# variable scope

variables defined inside a function is a local variable

print ==> returns only a text to be printed on the console. A fucntion that use prints at the output returns None, no value from the function can be used after.

return ==> return a value that can be stored in a variable and used later

note: a global variable (defined outside a function can be called inside a function but its value cannot be modified inside the function unless it has been passed as argument)
so you annot add values to a variable defined outside, you can only see the value of the variable, not increase or change it unless it has been passed as argument

# arguments values

def function_name(arg1, arg2=5)  ==> arg2 has a default value of 5, can be overriden if necessary

passer un argument à une fonction:

    function_name(taille=7, poids=5)
    function_name(5, 3)

On peut passer les arguments par position ou par nom


# docstrings:

1st line: used to document the **purpose of a function** """ triple quotes
2nd line (if needed): used to describe INPUT arguments
3rd line (if needed): used to describe RETURNED values

def population_density(population, land_area):
    """Calculate the population density of an area.

    INPUT:
    population: int. The population of that area
    land_area: int or float. This function is unit-agnostic, if you pass in values in terms
    of square km or square miles the function will return a density in those units.

    OUTPUT: 
    population_density: population / land_area. The population density of a particular area.
    """
    return population / land_area

# Lambda functions

simple one line functions called like this
double = lambda x: x*2

to call the lambda function is the same as a normal one: double(5)
we can have multiple arguments: multiply = lambda x, y: x*y

# Map() higher-order function
takes a function and an iterable as input and apply the function at the iterable 
list(map()) to obtain a list from the results.

list(map(lambda x: sum(x) / len(x), numbers))

# Filter() higher-order function
takes a function and an iterable as input and return an iterable for the items that returns true

list(filter(lambda x: len(x) < 10, cities))

# Generator functions
functions that return a stream of data that can be called one after the other. For this function we don't want to return once, but one item after each call. 
instead of "return" we use "yield" so that we return one element at each call (keeping in memory the last position)

Generators are useful when doing a list would not fit in memory or when the cost to calculate each list element is high and you want to do it as late as possible

def my_range(x):
    i = 0
    while i < x:
        yield i
        i += 1

for x in my_range(5):
    print(x)


Generators expressions:
like a list comprehension but with parenthesis, produces a generator instead of a list:

sq_list = [sq**2 for sq in range(10)] ==> produces a list
sq_list = (sq**2 for sq in range(10)) ==> produces an iterator



