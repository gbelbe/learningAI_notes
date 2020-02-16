# Python:

https://code.visualstudio.com/docs/python/python-tutorial


## basics

sensible à la casse et a l'indentation

attention : exponentiel ** pas ^
% = modulo (le reste lorsqu'on a divisé deux nombres)
// integer division (7//2 ==> 3 arrondis à l'entier le plus proche)

Assigner plusieurs variables a plusieurs valeurs (ex: des coordonnées:) x, y, z = 2, 3, 4 (au lieu de x = 2, y = 3, z = 4)

snake_case => Naming convention for python: casse petite et underscore => ma_variable

print(type(x)) donne le type de la variable (int...)
Attention quand on convertit un float en int ex: int(16/3) on n'arrondit pas le résultat, mais on obtient uniquement la partie entière du résultat.
Si l'on divise 2 ints, on obtient un float. Pour transformer un int en float, il suffit d'y ajouter un point sans rien après.

Pas d'espace juste après les parenthese ex: print(3 * 8) ou print(3*8 - 1)

string escape:
'"toto" et tata' ou l'inverse.
ou "\"toto\" et tata"
Concat avec signe +  ==> print("hello" + "world")
Repeter une string avec * ==> print("hello" * 3)  hellohellohello
len("helloworld") ==> nombre de characteres dans la string

Change type: str(variable) convert to string, float(variable) 

3 ways to work with variables:
Operators: var>3, (built-in)Functions: print(var), Methods: string.lower()
a method are functions that belong to an object. A string is an object for exemple.

ce que l'on met entre les parenthèses d'une fonction = un argument. Dans une classe, les fonctions sont ses méthodes, et l'object lui même est toujours le premier argument des methodes. Si l'on ne met rien, c'est l'objet lui même qui est passé comme argument (self).

Methods are called using a dot after an object. sample_string.lower()

formatter une string:
print("bonjour monsieur {}".format("billy"))

.split() ==> split method with whitespace and put the word in a list

boolean: True or False sans guillemets



## lists and data structures [,,]

Data structure = containers that organize and group together different types. (strings, ints...)
list is the most basic data structure. (**mutable ordered** sequence of elements)

string and lists are ordered, but only lists are mutable. It means that by changing its content we modify value of variables that are linked to it.

we can index a new element at the last place of the list by using  my_lit[-1]  (start at 0)

slicing a list ==> trouver une sous liste a partir d'une liste:

ex: liste_1["jan", "fev", "mar", "avril"]
liste_2 = liste_1[2:3]==> mars (premier élément inclusif, second élément **exclusif**)

list.len() length of a list, number of elements

index, in / not in and len() are both for string and lists

max()   greatest element in a ist 
min()
sorted() return the list sorted without changing the original list
print(sorted(my_list, reverse=True))

join() join a list into a string: 
phrase = " ".join(list)

liste.append("toto")

liste.pop() ==> enlève le dernier element de la liste

sum(liste) ==> renvoie la somme des éléments de la liste

### Zip

items = ["bananas", "oranges", "fraises"]
quantities = [3, 5, 15]
list(zip(items, weight))
==> [("bananas", 3), ("oranges", 5) ...
combine iterables in a sequence of tuples. 

ou for item, weight in zip(items, weights)

to unzip a list: use asterisk:  

manifest = [("bananas", 3), ("oranges", 5)]
==> items, weights = zip(*manifest)
print(items)
print(weights)

### Enumerates
items = ["bananas", "oranges", "fraises"]

for i, item in enumerate(items):
    print(i, item)




## python tuples (,)

store related pieces of elements (ex latitude , longitudes)
ex position = (1.03, 2.04) ou position = 2.4, 4.5 (parenthèses pas obligatoires)

used to connect together variables that comes always together.
tuples can also be used to assign multiple variables in a compact way: dimensions = 20, 30, 40 (sans parenthèses)
length, height, width = dimensions ==> tuple unpacking: les valeurs du tuple dimensions sont assignées à 3 variables l, h et w.

tuples are like list except they are immutable (cannot modify their content nor re-order them)



data = ((0, 1, 2), (3, 4, 5), (6, 7, 8), (9, 10, 11))

data_transpose = tuple(zip(*data))
print(data_transpose)

Output:

((0, 3, 6, 9), (1, 4, 7, 10), (2, 5, 8, 11))



## Sets {}

list of unique elements ==> mutable unordered collection of unique elements
fruit = {"apple", "banana", "orange"}
print("watermelon" in fruit)  ==> False
fruit.add("watermelon")
fruit.pop() ==> remove random element from fruit (as sets are unordered)

liste = ['toto', 'toto', 'billy', 'joe']
unique_liste = set(liste)
print(len(unique_list)) ==> 3

set supports "in", but no append, instead use add
be careful as set is unordered, so there is no last element...

set values cannot be accessed through indexing, nor sliced, as there is no order in a set.


## Dictionary {:,:,}

list with key:value pairs, you can refer to the value with its key not only with its index value.
key is str int or other immutable types

elements = {'air': 1, 'helium': 2}
elements['lithium'] = 3

elements.keys() get keys in a dict


check if an element is a key in a dictionnary

lithium in elements ==> check if lithium in elements

print(elements['lithium']) ==> return 3, but can return error if lithium does not exists, better use "get"
x = elements.get('lithium') ==> return value or 'null' if nothing is returned, not error
not_null_value = x is not None

sorted(list(verse_dict.keys()))
On récupère les clés d'un dicitonnaire dans une liste, que l'on range par ordre alphabétique.

max(verse_dict, key=verse_dict.get ))
on récupère la clé qui possède la valeur la plus importante. key=dictionnaire.get ==> on récupère la valeur de la clé


### to iterate on both key and values of a dictionary

for key, value in dictionary.items():
    print("actor: {} and role {}".format(key, value))

(use the built-in dictionary method items)

iterate through key and values of a dictionary
    for name, score in scores.items():


## Control flows

### If

if season == "winter":
    print("toto")
elif season == "summer":
    print("billy")
else:
    print("other")

### Boolean
If should be followed by a boolean expression, if checking directly a boolean variable we can do it directly:

if is_black:
    code to play
(no need to do if is_black == True:)

if 2 conditions:

if weather == 'cold' or weather == 'sunny':  (et pas if weather == 'cold' and 'sunny')

Python evaluates to False for 0, or "", None, "", [],{}

errors = 3
if errors:
    print("there are {} errors".format(errors))


## LOOPS

For loop:

For city in cities:
city is the element or iteration variable and cities is the name of the iterable (a list, set, tuple or dictionary)

to iterate inside a list, we use range function:
range(10)==> list of numbers from 0 to 9
range(1,10,2) 1 starting number, 10==> 9 is the last number, 2 => step from 2 to 2)


### to create a new list based on another list:

cities = ["new york", "paris", "hanoi"]
for city in cities:
    capitalized_cities.append(city.title())


### to modify elements of a list:

for index in range(len(liste)):
    liste[index] = liste[index].capitalize()


for i in range(3):
    print("hello")

### to create a dict based on a list, counting its elements:
book_title =  ['great', 'expectations','the', 'adventures', 'of', 'sherlock','holmes','the','great','gasby','hamlet','adventures','of','huckleberry','fin']

book_count = {}
for book in book_title:
    if book not in book_count:
        book_count[book] = 1
    else:
        book_count[book] +=1

or 

for book in book_title:
    book_count[book] = book_count.get(book, 0) + 1 




while loops can be useful to wait for user input: while user_input == 'y':

### break / continue

if we want to break following a condition:

for cargo_name, cargo_weight in manifest:
    if weight >= 100:
        break

use continue to skip elements matching a condition:

    elif weight + cargo_weight > 100:
        print("  skipping {} ({})".format(cargo_name, cargo_weight))
        continue        


## list comprehensions

iterate through a list and create a new one in a single line:

cities = ["paris", "new york", "london"]
cities_capitalized = [city.title() for city in cities]

or sqr = [number**2 for number in range(9)]
on peut rajouter une condition sqr_impairs = [n**2 if n%2 == 0 for n in range(9)]
