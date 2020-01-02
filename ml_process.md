#General concepts


## machine learning: 
a program tries to learn a way to resolve a problem by discovering an algorithm based on data only. There is no deterministic algorithm written by a programmer to tell the computer how to resolve the problem

deep learning = neural network with more than one hidden layer

### supervised learning: 
algos trained with labeled exemples as input where the output is known

phases: 

data acquisition => data cleaning => model training and building => model testing => model deployment

1) we split data into 70% training data and 30% validation and testing data
2) we "fit" a model into the training data (so that data fits the model the best)
3) we run the model with the validation data and compare the prediction with the real results
4) we adjust the model parameters to try to have a better fit on the test data. > i.e. we add more layers or more neurons => and reloop to the 3
5) we test the model with test data
6) we deploy the model to the real world

### unsupervised learning:we

we don't have or don't know the correct answer or label for historical data
evaluation is much harder, no test set either as nothing to compare with.

Images or information / row data without labels:
==> clustering : grouping together unlabeled data points into clusters
                    data points are assigned to a cluster based on their similarity
                    the model will try to cluster images / data based on similarity. we don't know which category or which kind of similarity the model will find
                    it is hard to evaluate the model performance.
==> Anomality detection
                    ex: find points that are very dissimilar to the rest (potential frauds) ==> if we don't have the labeled data of what is a fraud.
==> Dimensionality reduction

### reinforcement algorithm

AI that is learning depending on what success or error it encounters while discovering new inputs. (ex: learns to walk, learns to play a game)
it must start again and again and receive positive or negative feedback depending on the actions it takes


### overfitting
adjust too finely to the training data and even the noise data. it will perform poorly (large variance) to the validation data (theorème de nyquist)
too many passes on the training set => testing data is not working as well, model is not working for data it hasn't seen before
don't train too much on training data
monitor training data vs test data: when error on testing data starts to increase, it is a good indication we are overfitting the model
this is called the cutoff point that determines the numer of epochs to train the model

=> increase in errors in the test set while the performance in the training set is still going down ==> indication we are overfitting the model

### underfitting
too simple model: will have average result performance, low modelisation of the underlying data trends

good model reduces error with the quantity of training data it enconters
training time = 1 epochs => passing the training data 1 time through your model



# Supervised learning: 2 types of models

## classification models

### Metrics : Accuracy, Precision and Recall and F1score

predict the belonging of a thing to a specific category (binary classification : true or false  vs multiple classes )

classification metrics:
- accuracy = number of correct predictions / total predictions  (good if the model classes are well balanced ex: 50% imgs of dogs and 50% of cats)
                if the test set have 99% of dogs imgs and 1 cats img it can look very accurate even if it misses all cats (99% accuracy)


If the model (or the decease being tested) is not very well balanced in the global population, we need to take into account other metrics than the precision:
pour certains modeles (ex detecter une maladie, on voudra maximiser le nombre de maladies détectées, et on préferera accepter un taux plus élevé de faux positifs et limiter
au maximum le nombre de faux négatifs. Donc on ne recherche pas toujours la précision globale du modèle mais de réduire au max la quantité de faux négatifs. Les fauts positifs iront faire le test clinique. ==> donc les indicateurs a prendre en compte ne sont pas toujours simplement la précision du modèle, mais un objectif détaillé doit être fait avec le business


- recall = ability of a model to find all the relevant classes within a dataset (vrais positifs / vrais positifs + faux négatifs)

- precision = ability of a model to find only the relevant data points (vrais positifs / vrais positifs + faux positifs=

- f1 score: combinaison entre precision et recall  ==> harmonic mean (sorte de moyenne qui réduit l'importance des valeurs extrêmes de precision et de recall) 
                    F1 = 2* (precision * recall) / (precision + recall)



## regression models

statistical measurement that determines the strength of a relationship between one dependant variable Y and a series of other independant variables
for ex: find covariance and correlation between these variable (ex you don't want stocks that are correlated to the one that you own)
regression task: the model attempts to predict a continuous value: 
- predict the price of a house given its features

### Metrics

root mean squared (RMS) used to punish larger errors.  racine(y-ŷ)²
compare the RMS value with the avg label value in your data set  ==> ex: rms of 10$ is very good if we try to predict the price of a house, but bad if it is for a candy




# activation functions
==============================

## for binary classification or linear regression (0 or 1 or a value between 0 and 1)

function that ==> what output given the input

perceptron : z = wx + b

### step function==> 1 if z>0  or 0 if z<0
    basic for binary classification, but very strong not so good for regression. 

### sigmoid function 
    varies between 0 and 1 more smoothly : logistic function

### hiperbolic tan
    similar to sigmoid but between -1 and 1 instead of 0 and 1 for the sigmoid
    tanh(z) 
 
### Relu (rectified linear unit) max(0,z)  
    if z< 0  ==> 0
    if z> 0  ==> returns z

    ReLu is very performant and most often used.



## activation function for multi-class classification

    output layer will have multiple neurons.
    non exclusive class classification
    mutually exclusive class classification (only one class for a data point)

    One output node by class ==> final output layer has many neurons (one per class)

### one hot encoding / dummy variables 
    
    one hot ==> 1 means on / 0 means off 

    binary classification for each class
    binary matrix for each color: each color is 0 or 1 if it is present 
    (if red, green or blue ==> blue is 001 , red is 100)

    we can do the same principle for non exclusive categories, but can be 110...

    1) non exclusive class classification ==> setting multipe tags to a photo

        Activation function ==> Sigmoid ==> each neuron will output a variable between 0 and 1 (probability of having that class)
    

    2) mutually exclusive: define if black&white or color 

        SoftMax activation function: calculate the probability distribution of eachh target class over all possible other target classes.

        range btw 0 and 1 ==> softmax sum of all numbers in each class => 1  , we return the only class with the highest probability



# Cost (loss / error) functions and Gradient descent

On teste divers poids et biais pour les fonction des neurones que l'on passe à travers la fonction d'activation; celà donne une prédiciton ŷ que l'on compare avec les données réelles pour savoir quel est la précision de la prédiction. 

Une fois fait, on change les poids et on recommence jusqu'à ce qu'on arrive à un optimum

y = true value
a = neuron's prediction
w*x + b = z
p(z) = a (a = activation layer output) ==> on passe z à la fonction d'activation


Cost function ==> C = moyenne quadratique des écarts entre la valeur réelle et la valeur qui sort de la fonction d'activation de la dernière couche de neurones du modèle

Les fonctions de couts ont de nombreuses dimensions car elles ont un grand nombre de neurones et de variables d'inputs.

## Attention: pour les problemes de classification multi classes:
On utilise la fonction de cout "cross entropy loss function" et pas la quadratique simple. (cross entropy car on assume que chaque classe a une distribution propre)


## gradient descent:

gradient = slope ==> pente de la tangeante à la fonction de coût
NOTE: Gradient ==> l'équivalent de la dérivée pour un vecteur de N dimensions
gradient descent: on calcule la dérivée de la fonction de couts avec tout ses Poids (W) et biais (b)

On teste des valeurs de la fonction de cout pour atteindre le minimum. On descend par "pas", en observent la pente de la tangeante à la fonction de cout (la dérivée de la courbe). Plus la pente est proche de 0 plus on est proche du minimum de la fonction. Plus le pas est petit plus le temps qu'il faut pour atteindre le minimum est long. Mais si l'on prend des pas trop élevés on risque de dépasser le minimum.

Ce "pas" ou "step size" est connu sous le nom de ##learning rate.
On a le même fonctionnement pour les matrices de "biais", pour trouver les biais qui minimisent la fonction de coût.

Pour gagner en efficience, (réduire le temps de calcul du minimum de la fonciton cout) on peut adapter progressivement la taille des pas: "adaptative gradient descent"
on réduit la taille des pas au fure et à mesure que la pente diminue.

Adam : one of the best gradient descent algorithm ==> adaptative and optimized way of performing gradient descent (found in 2015)

(n dimensions vectors = tensors)



## maximum likelihood estimation:

methode qui détermine les valeurs des paramètres d'un modèle: ils sont choisis pour qu'ils maximisent la chance que le modèle produise les données effectivement observées.
[ a partir d'un modèle déjà trouvé, on optimise ses paramètres pour qu'ils maximisent le fit avec les résultats réels ]
on part du principe que les paramètres sont indépendants entre eux.

## cross entropy
une fonction de cout utilisé lorsqu'on a plusieurs classes différentes. Il compare le résultats pour chaque classe donnée par le modèle en probabilité que la classe existe ou non, comparé avec le fait qu'elle existe ou non (0 ou 1 avec le one -hot encoding)


## back propagation

Backpropagation is the process of passing the error from the last Layer through the former layers of the network and adapting the weight and bias accordingly.
=> calculate the error term at the last layer
=> going backward through the network to calculate all those errors at each layer
=> adjust the weight and biases accordingly to minimize the cost function


https://www.miximum.fr/blog/introduction-au-deep-learning-2/

https://www.youtube.com/watch?v=6BMwisTZFr4&t=17s



Data normalization:
========================

To prepare data around matrixes, it should be normalized (i.e. feature scaling)
this is to ensure that all the data is on a similar scale.

Starting with a matrix of big integer numbers (100's of lines and columns)
ex: mean normalization: ex distribute all the data between 0 and 1 evenly


Data separation:
=======================

After data has been normalized, it is split into 3 sets:
1) training set (60% of the data)
2) cross validation set (20% of the data)
3) test set (20% )

we select randomly rows from the original data matrix, and make sure that the same rows are not selected in more than one set.

np.random.permutation(N) creates a random permutation of integers from 0 to N-1

we can get the number of rows of a ndarray, by checking its shape. (shape is a tuple, so we can get only its rows or columns like this:)

X_norm.shape ==> (1000, 20)
row_indices = np.random.permutation(X_norm.shape[0]) ==> we ask for a random 1d array of 1000 elements (as it takes 1000 from the number of column from the shape of the ndarray.







Data analysis and cleaning (outliers, NaN, missing values...)
======================== 

Pandas Series and DataFrames are designed for fast data analysis and manipulation, as well as being flexible and easy to use


    Allows the use of labels for rows and columns
    Can calculate rolling statistics on time series data
    Easy handling of NaN values
    Is able to load data of different formats into DataFrames
    Can join and merge different datasets together
    It integrates with NumPy and Matplotlib

For these and other reasons, Pandas DataFrames have become one of the most commonly used Pandas object for data analysis in Python.


Pandas series is an array that can hold different data types. 
We can add a label to each element in the serie.
