#Linear boundaries:

## Boundary line

2 facteurs utilisés pour l'entrée à une univ:
Resultat d'un exam + moyenne de l'année:

W1x1 + W2x2 = b
or
w1x1 + w2x2 + b = 0

w = (w1, w2) vecteur w
x = (x1, x2) vecteur x

wx + b = 0 ==> boundary line ==> wx produit des deux vecteurs

y = label: 0 ou 1

ici si l'étudiant est accepté => y = 1, sinon y = 0
ŷ (y chapeau) est la prévision que l'algo prédit ==> wx + b > 0  ==> ŷ = 1

## Boundary plane

3 facteurs utilisés pour départager un résultats:

w1x1 + w2x2 + w3x3 + b = 0

similarly

wx + b = 0

## perceptron

takes N variables, multiply them by a determined weight, and returns 0 or 1 depending on the result of these scores on the linear equation of the perceptron

Wx + b = [sum from i=1 to n](WiXi) + b

Step function: the function returns 1 if the input is positive, and 0 if the input is <= 0


### combination of nodes:

1st node calculate a linear equation of the inputs x weights 
2nd node applies a step function to the result

Summation sign ==> linear equation in the first node
then Step function 


### Perceptrons can be also logical operators:

perceptrons can be of type AND: they will be true only if the results of the two previous perceptrons are true

### perceptrons holds a function that tries to classify the entry values and gives a binary answer to the question.

This form is an equation. Firstly it is set randomly, and them we look for misclassified points, and try to modify the equation to move the line towards classifying it better.

Generally if the point is above the line, we should substract the coordinates values to the equation, if the point is below the line, we should add the coordinate.
to make it graduative, we multiply these coordinate by a "learning rate" (ex: O,1) for the moves to be less extreme


## step function to sigmoid function 

step function is used to treat discreate "binary" result, if x < 0 answer is 0, if x > 0 answer is 1

if we want the result to be a probability we pass the result of the perceptron to a Sigmoid function that will give a probability, when it is close to 0, probability will be 0.5, when it is large positive, it will be close to 1, when it is large negative, it is close to 0.


## in the case we want various results, not simply 0 and 1: we use the softmax function
will give the probability of being one of different values.

## encoding different possibilities into numeric values: one hot encoding

when we want to see the probability to be a cat, a  dog or a mouse, we use each of these possibilities as a separate column and we check for each column the probability for it to be true

## maximum likelihood of a model:

for a given equation (model), we calculate the probability of a point being red or blue.
If the point is red, we calculate the probability of it being red (or ! blue)
if the point is blue we calculate the probability of it being blue.
we multiply all of these probabilities to get the total probability of the model for the set of points
for the same points, we evaluate the maximum likelihood of all the models, to pick the one that give the highest probability, for the same set of points.

the method of increasing the total probability of the model given the actual set of points is called "maximum likelihood"


## Cross entropy

For large number of data points, working with multiplication is not easy to calculate, so we use log to convert it to a sum.

log(a*b) = log(a) + log(b)

0,6 * 0,2 * 0,4 = 0.0034
ln(0,6) + ln(0,2) + ln(O,4) 
-0,51 -1,61 -2,3 ...

but log(1) = 0 donc comme on a des probabilités = donc uniquement des nombres inférieurs à 1, celà nous donnera uniquement des nombres négatifs.

donc on décide de mettre un - au lieu d'un +, pour obtenir l'erreur

La Somme des négatifs des logs des probabilités s'appelle la cross entropy, plus sa valeur est petite, plus le modèle est performant
Good model = low cross entropy
Bad model =  high cross entropy

each point that is well classified gets small value, each point that is wrongly classified gets high value... so the model that performs the best has the lowest total cross entropy

Our goal moved from increasing the probability of the model to reducing the crosse entropy of the model
Error function = cross entropy

## error function

to calculate the probability that the prediction is true:

if the point is well classified as true => value ŷ = P(gift) = 1   ==> models predict that behind the door there is a gift  
if the point is well classified as false => value ŷ = 1 - P(gift) = 0  ==> models predict that behind the door there is no gift

Error : in the first case:  error = -ln(ŷ)

