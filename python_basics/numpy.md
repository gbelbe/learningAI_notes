in numpy, nd arrays are n-dimensional arrays.
numpy create list of elements with all the same type (different than lists)
numpy will upcast the type from the more precise needed one. We can force a datatype if we need

We can create a nd array from another array like object (ex: python list) or using a numpy function that generates an array.

import numpy as nd
x = nd.array([[1, 2, 3], [1,2,2]])

print(type(x)) ==> numpy ndarray

x.dtype ==> type of the numbers inside the array (int64)

x.shape ==> how many rows and columns there is in the array (2,2)

x.size ==> 4

Array with n dimension ==> array of rank n
matrix = 2 dimensional array with rows and columns
identity matrix = matrix avec le meme nombre de lignes que de colonnes, qui a un dans sa diagonale et des 0 partout ailleurs

np.eye(5) ==> 5 x 5 identity matrix

We can save a numpy array to a file ==> np.save('my_array', x)
this save the array x to a file "my_array.npy"

we can load it later with:
y = np.load('my_array.npy')

## shortcuts

Once you have a numpy ndarray you can access to a lot of methods, simply by accessing your matrix with a dot and press "tab" on jupyter notebook.


## create a matrix of ones

np.ones((4,4)) create a matrix of 1 of 4 rows and 4 columns

##arange create values from a to b with a step
np.arange(start, final, step) create an array with numbers from the first to the final at a specific step (default 1)

##linspace create values equally split between 2 numbers
np.linspace(start, final, number-of-points) split the number of points between start and final evenly

We can create n order matrix by reshaping a single line array:

##reshape an array into another
np.reshape(x, (2,5)) ==> rehape the array x with 2 lines and 5 columns:
note==> to reshape the array we need to be sure to provide the same number of elements that the original single line array


Random matrix can be used to initialize the weights of the model.
np.random.random([2,5])
create a 2x5 matrix of random numbers between 0 and 1
np.random (access to random module in numpy)
np.random.random(5)

========================>

##access
to access a np array x, we can access its elements by x[5] ==> 6 position, the first one being x[0]
x[-2]  ==> second position starting from the end

for multi dimension array: x[0,0] access the first elem of the first row


##np.delete

x = np.arange(1,20)
x = np.delete(x, [3,4,5,10])
supprime les éléments 4,...et 11 de l'array

pour une matrice à 2 dimensions:
y = np.arange(1,10).reshape(3,3)
np.delete(y, 0, axis=1) ==> supprime la premiere colonne
np.delete(y, 0, axis=0) ==> supprime la première ligne
np.delete(y, [0,2], axis=1) ==> supprime la première et la troisième colonne
np.delete(y, [0,1], axis=0) ==> supprime les deux premières lignes

##np.append

np.append(x, [3,4]) ajoute les éléments 3 et 4 à la fin d'un array a une dimension

np.append(x, [[3,4,5]], axis=0) ajoute une ligne avec les éléments 3,4,5 (attention aux doubles crochets

np.append(x, [[2],[3],[4],[5]], axis=1) ajoute une colonne avec les elems ! il doit y avoir autant d'éléments qu'il y a de ligne....

##np.insert

np.insert(x, 3, [2,3]) insère 3 entre l'élément 2 et 3

..

##np array stacking

vstack and hstack, stack together np arrays horizontally or vertically
be careful as the shape of the arrays must match

np.vstack((x,y)) stack vertically array y under array x (add y as the last line of array x)
np.hstack((x,y)) stack horizontally array y after array x, (add y as a column of x)
for these operations to happen, need to reshape y array to fit as a column of x:

ex x.reshape(4,1) change l'array x en 4 lignes et une colonne pour le préparer à le stacker à un autre array de 4 lignes et n colonnes


## Slicing ndarray

starting index included, ending index excluded

ndarray[start:end]
for 2 dimensional array:

x= 
[1  2  3  4  5
 6  7  8  9 10
11 12 13 14 15
16 17 18 19 20]

z = x[1:4, 2:5]
a gauche de la virgule, quels sont les index que l'on prend sur les lignes,
à droite de la virgule, quels sont les index que l'on prend sur les colonnes.
==> Index commence à 0 et finishing index inclusif (4 et 5)

https://thispointer.com/python-numpy-select-rows-columns-by-index-from-a-2d-ndarray-multi-dimension/

donc prend les lignes 2, 3 et 4 et les colonnes 3, 4 et 5

celà donne :
[[8 9 10]
13 14 15
18 19 20]]

##slicing from an index array

Si l'on veut prendre quelques lignes d'un array:
x = np.arange[16].reshape(4,4)
row_indices = np.array([0,2,4]) ==> index des lignes que l'on veut selectionner 
z = x[row_indices, ]

ou x[[0,2,4], ]


## Be careful, assigning a slice to a new variable only creates a view to the original array. If the original or the new array changes, both changes.

If we want 2 arrays to be linked (the original and the slice) we only affect the slice to a new variable

##Copy ==> If we want them to be independant, we must use the copy method

z = x[1:4, 2:5].copy()
or z = np.copy(x[1:4, 2:5])

## np.diag

extract the diagonal of an array
np.diag(x) ==> grab the main diagonal
np.diag(x, k=1) ==> grab the diagonal above the main (-1 = below)

## using array to slice other array:

indices =  np.array([1,3])

use the indices array to select the second and 4th row of the y array. (_:_ means all the columns)

y = x[indices, :]

## unique elements of an array

np.unique(x) ==> donne un array simple avec les valeurs uniques de l'array x

## boolean indexing

in case we don't know the indices of the elements we want to retrieve
we want them to match a condition

ex: print(x[x>50]) renvoie les éléments de la matrice x qui sont supérieurs à 50

print(x[(x>50) & (x<=59)])

x[(x>50) & (x<=59)] = 888 ==> modify all elements betw 50 and 59 to 888


## operations on arrays

np.intersect1d(x, y) ==> gives a new array with only the similar elements of two 1d arrays

np.setdiff1d(x, y) ==> gives a new array with only the different elements

np.union1d(x, y) ==> gives a new array with all unique elements from two arrays

## sorting

np.sort(np.unique(x)) sort all unique values from x

np.sort(x, axis=0) ==> sort by column > or axis=1 to sort by row 


## element operations

x = np.array([1,2,3,4])
y = np.array([5,6,7,8])
print(x+y)
np.add(x,y)
return a matrix with the sum of each elements

np.multiply(x, y)
np.mean(x) or x.mean()

arrays must have the same shape or be broadcastable

print(np.sqrt(x)) square root of elements or x
print(np.exp(x))  exp...
print(np.power(x, 2)) elevate elements to the power of 2

sum of columns ==> x.sum(axis = 0)
sum of all lines ==> x.sum(axis = 1)

print(x - 3) ==> substract 3 to each element
numpy is working to broadcast 3 to all the elements of the array


==> numpy is able to broadcast a small array along a bigger array:

y = np.arange(9).reshape(3,3)
x = np.arange(3)
print(y + x) ==> add the to each line of the 3x3 array the 1x3 array elements


