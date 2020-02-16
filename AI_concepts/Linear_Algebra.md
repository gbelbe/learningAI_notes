# vector space

Physics: vectors are arrows
Computer science: vector are matrix (list) with numbers
Maths: You can add or multiply both matrix or vectors

## notation:

vectors are represented with [x, y] ==> different to points which are represented with parentheses(x, y)

## vectors addition:

move the second vector so that its starting point is at the end of the first vector.
draw the resulting vector from the origin to the end of the second vector.
On a matrix, this leads to the addition of x and y of both matrix.

## vector multiplication by a number ==> Scaling

When we multiply a vector by a number, it becomes a "scalar", scalar by extension is the number by which we multiply a vector or matrix.

Multiply [2, 3] by a scalar (4) ==> [2x4, 3x4]

Element of a vector = component = coordinate.

A vector of n elments defines an n dimensional vector and belongs to R^n.
To calculate the direction of the movement, we use an angle

## vector transpose

column vector and row vectors are transposed:

Transposed column vector is the equivalent of a row of the same elements (and vice versa) ==> symbol [ a1 a2 a3 ]T


# Magnitude and direction

a vector holds a magnitude and a direction ||z|| magnitude of vector Z.
for the magnitude of a 2D vector ==> pythagore: ||z||^2 = a1^2 + a2^2

angle==> relative to the horizontal axis

Teta = Tan-1(y/x)

(socahtoa==> sin = oppose sur adjacent, cosinus = adj / hyp, tan = opposé / adjacent)

# î et ĵ sont les vecteurs unitaires (basis vectors) î sur la l'axe des abscisses et ĵ sur les ordonnées.

pour reconstituer un vecteur [3, -2] on multiplie î et ĵ par les scalaires correspondants aux coordonnées

Linear combination of the 2 vectors = aî + bĵ  ou a et b sont les scalaires et î et ĵ des vecteurs de base du système de coordonnées

Span of vectors (sous espace vectoriel): quand on pense à tous les vecteurs qui alignés sur une droite, on parle d'une droite
1 vecteur ==> une fleche, une collection de vecteurs : chaque vecteur est un point (fleche dont l'origine est à 0)
quand on pense à tous les vecteurs possibles sur un espace à deux dimensions on parle de plan vectoriel

Dans un espace à trois dimensions, le span de deux vecteurs représente un plan vectoriel

2 lienarly dependant vectors ==> on the same axis, one can be expressed with a linear combination of the other (the other x a scalar)

If each vector adds another dimension to the span, they are said to be linearly independant

**The basis of a vector space is a set of linearly independant vectors that spans that space**

2 lineary dependant vectors corresponds to 2 equations representing the same line, they will not solve for one element, but for an infinite number of elements

# Matrix

A matrix has m rows and n columns mn matrix (toujours le nombre de lignes en premier)
a matrix of one row or one col is a vector (row vector or col vector)

## matrix addition: 

- verify that matrices are of the same dimensions
- make sure we add elements of the same corresponding indices

a matrix of dimensions m x n can only be added to a matrix of the same dimensions, then we add each elements of the 2 matrices

## matrix multiplication by a scalar

- no need to verify dimensions nor indices, simply multiply the scalar by each element the matrix

D =  0,2A -5B -2C ==> linear combination of matrices and scalars (A, B, C D = matrices) 0,2, -5 and -2 are scalars

## 2 matrix multiplication 

dimensions needs to be aligned. Square matrix, same number of dimensions (rows and columns)

Each element of the resulting matrix is the sum of multiplying all elements in row i of first matrix with the elements of row j of matrix 
Sum of (1ere ligne Mat1 x 1ere col Mat2 + 1ere ligne M1 x 2eme col M2 + 1ere ligne M1 x 3eme col M3...)
sum of (2eme ligne M1 x 1ere col M2...)

Matrix multiplication is not commutative as AxB != BxA (although scalar multiplication is commutative)

-5*-1+4*-1+4 > 5

3*2+ 2 + 8 > 16

Matrix multiplication of non-square matrices is possible if matrix A row nr = matrix B columns nr


PxQ is possible is P col number = Q row numbers


a) 5 rows
b) 3 cols
c) c13 ==> 0.6*-4+88+20+98*5
d) c = BxA ==>  not possible


Linear tranformation:
function that transforms a matrix set of vectors
all lines must remain lines (linear) and the origin must remain the same.

To deduce where the original vector will land after a linear transformation, it is important to follow where î and ĵ lands after the transformation, 
as then it will be only applying the same rule (linear multiplicaiton of î and ĵ with a scalar) to obtain the new vector after the transformation.

î ==> [ 1 -2] transformation de î 
ĵ ==> [ 3 0 ] transformation de ĵ

on peut ensuite facilement obtenir le transformé de n'importe quel vecteur [x y] ==> x[1 -2] + y [3 0]
x fois la transformation de l'axe de base î
y fois la transformation de l'axe de base ĵ
donne la transformatrion du vecteur d'origine

A 2 dimensional linear transformation is described by 4 numbers: 
the 2 coordinates where î arrives
and the 2 coordinates where ĵ arrives

Une Transformaiton linéaire est généralement décrite par une 2x2 matrix colonne des nouvelles coordonnées de î, colonne des coordonnées de ĵ

si l'on veut appliquer la transformation linéaire a un vecteur, on multiplie ses coordonnées par la matrice de la transfo linéaire

on additionne la version scalée de ce vecteur avec les nouvelles coordonnées


La première colonne de la matrice d'une transformation linéaire correspond aux coordonnées ou le premier vecteur de base arrive (î) la seconde colonne correspond à la second 


si les î et ĵ d'une matrice de transformation linéaire sont sur une même droite (linearly dependant vectors) alors on n'est plus sur un plan vectoriel mais sur une simple droite

Matrices est un langage pour décrire la transformation de l'espace: les colonnes sont les coordonnées de la transformation des points des vecteurs "bases" du plan vectoriel (î et ĵ)

Matrix vector multiplication is just a way to calculate what that transformation does to a given vector

A matrix is a transformation of space, linear algebra is taking into account that space transformation to see how they affect different vectors.



## Neural networks

in a neural network there is a input matrix, various hidden matrix layers and an output matrix.
relationship (lines) between these layers are a scalar coefficient that is connecting a neuron to the next, it is called a weight
these lines connect a neuron in a layer to all the neurons in the next layer

Since there are many weights connecting a layer to the next, we represent them into a matrix of weight

==> when we train the NN, we look for the best values of these matrix of weights

hi (hidden neuron value) = F(xi [input neurons] * Wi [weight])

==> sum of [previous neuron layer values] * [weight of each value] (symbolised by the connecting lines)  + bias (parameter of the neuron = integer) ==> 
this summation goes to an activation layer, before providing the output

### 2 phases of NN

1) Training
training set =  many pairs of inputs and their corresponding ouputs ==> objective of finding the optimal set of weights that maps the inputs to the outputs

    1.1 ==> feedforward cycle (vector by matrix multiplication followed by activation function)

    From the input state and the weights, Calculate the value of the hidden states, then calculate the value of the output values.

    Input vector = matrix of input neurons,
    Weight matrix = multi-column matrix of weights (as each input value is multiplied by a different weight to give the result matrix (ex the hidden layer)

    each sum of multiple input values by their respective weight values, matrix multiplication, it passed through an activation function to give the proper result value.
    h1 = P (activation function) (x1*W11 + x2*W21 + x3*W31...)
    h2 = P(x1*W12 + x2*W22+...)
    ...

    ex 3 inputs 

    h1 = Fi( x1*W11 + x2*W21 +x3*W31)
    


    1.2 ==> backpropagation


2) Evaluation
we use the network obtained in the training phase, apply our inputs, and test our outputs

