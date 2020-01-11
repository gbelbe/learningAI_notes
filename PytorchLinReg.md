#Linear regression with Pytorch


avec pytorch, on peut gérer un "dynamic computational graph", un lien entre plusieurs tensors liés entre eux par le réseau de neurones.

1) tensor avec option autograd pour calculer la dérivée automatiquement.

calculer la dérivée sert à "remonter en arrière". La dérivée partielle de chaque poids des synapses sur la fonction d'erreur permet de trouver les poids à modifier le plus ou le moins pour réduire la valeur de la fonction d'erreur. C'est ce qu'on appelle la backpropagation. On utilise la dérivée en chaîne pour retrouver les dérivée partielles pour chaque poids à partir de la dernière couche de neurones.


X = torch.tensor(3., requires_grad=True)  ==> on définit x = 3 et on demande au graph de suivre les paramètres de toutes les fonctions liées à x.

y = X**3 + 3*X**2 + 5

y est une fonction basée sur le tensor X, qui sont liés dans un graph.
le fait de mettre requires_grad= True va permettre à pytorch de calculer en permanence les dérivées.

y.backward()  ==> calcule la dérivée première de la fonction y

x.grad  ==> calcule la dérivée au point x.

pour la backpropagation: on va calculer la dérivée de la fonction coût au point x. C'est la pente de la fonction Y au point ou x=3.

Gradient: position de la dérivée d'une fonction pour une certaine valeur de x.



Lorsque l'on a plusieurs couches qui sont basées les unes sur les autres, le fait de faire : 

dernièreFonction.backward()

puis x.grad ==> donne la dérivée de la dernière fonction par rapport à la première avec la chain rule en plaçant, par rapport à l'input x


## sometimes we don't need to track computational graph, then requires_grad=False (for exemple if we reuse other tensors from other models)


note pour plotter des points x et y a partir de deux colonnes, on convertit les tensors en numpy ==> X.numpy()




# torch.nn

import torch.nn as nn

model =  nn.Linear(in_features=1, out_features=1) (on a que x et y en input et output features)

print(model.weight)
print(model.bias)

model.weight and bias are defined randomly as tensors with requires_grad set to true



plt.scatter(x, y) ==> plot all points in a graph
plt.plot(x, y) ==> plot a function (line, not points)


1) loss function
criterion = nn.MSELoss()   ==> Mean Square Error Loss (cost function for linear regression)
Par convention la fonction d'erreur est appelée "criterion"

2) optimization
torch.optim.SGD(model.parameters(), lr=0.001) (SGD stochastic gradient descent, lr =  learning rate)

3) training the model

epochs = 50
losses = [] (on crée un placeholder pour suivre l'erreur en fonction des passages de données (epochs) ==> 1 er passage on change les paramètres, 2nd passages... 

for i in range(epochs):
    i +=1

    y_predicted = model.forward(X)

    loss = criterion 


Loss function ==> appelée "criterion" car c'est le critère sur lequel on va optimiser la fonction.

Optimizer ==> c'est le mécanisme qui va optimiser la fonction de cout, donc souvent un "gradient descent"

optimizer =  torch.optim.SGD(model.parameters(), lr=0.001)

lr = learning rate
SGD stochastic gradient descent

epochs: entire pass of the data set.
on passe la première fois une epoch, on calcule l'erreur, on change les poids, puis on repasse une epochs avec les nouveaux poids, et ainsi de suite.

On peut utiliser un array "losses" qui va enregistrer la valeur de "criterion" la fonction erreur après chaque epoch.

C'est bien d'imprimer la valeur de la fonction d'erreur pour voir si elle converge après un certain nombre d'epochs. 




==> corrélation linéaire:

Erreurs: moindre carrés (gauss)

Corrélation ==> r = +1  si la fonction monte et inclue les données, r= -1 si elle descend et contient les données ==> proche de 0 si les données sont très loin de la droite

Attention ==> "correlation n'implique pas causalité"  ==> un lien entre deux variables = corrélation les variables bougent ensemble

la corrélation définit la performance de la régression linéaire pour prédire un nuage de points

r² = coefficient de détermination


régression linéaire de dimension 2: on cherche a prédire le label y a partir des features x1 et x2: dans ce cas la régression linéaire consiste à trouver le plan qui colle le mieux à cet espace de points

la regression linéaire de dimension d = calcul d'un hyperplan de dimension d dans un espace de dimension d+1 qui colle le plus a un nuage de poins
