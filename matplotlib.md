
a clean dataset:

each variable is a column
each observation is a row
each type of observation unit is a table

attention aux colonnes qui comportent des valeurs de données, indicateur de données mal organisées


%matplotlib inline ==> enable graphs to be displayed directly in notebooks

sb.countplot(data=dataframe, x='column_name')

plots can help us find out if data is uni modal or multi modal (not centered around one mode)

#Scatterplot = nuage de points (2 variables quantitatives)

relationship between 2 quantitative variables
plot: (x,y) x = valeur de la premiere variable, y valeur de la deuxieme

mesure de la force de la corrélation entre deux variables = coef de correlation
(le plus commun = coef de pearson ==> r  pour des corrélations linéaires)
stats entre -1 et 1 ==> r proche de 1==> les deux variables vont dans le meme sens, r<0, les deux var sont corrélées en sens inverse


##Si notre objectif est de créer un modèle de régression sur nos données, scale transformation can be used to modify a non-linear correlation in the original unit to a linear one on the transformed unit

import matplotlib as plt
plt.scatter(data = fuel.econ, x= 'var1', y= 'var2')
plt.xlabel("displacement")
plt.ylabel("label2")

import seaborn as sb
sb.regplot(data = 'dataframe', x='var1', y='var2') ==> similar as scatter but with regression line

Si le nuage de points est floue, on fait du random sampling (pour réduire le nombre de points sur le graph
ou on utilise la trensparence pour que les points superposés soient plus ou moins noirs en fonction du nombre de points supperposés
ou on uttilise le "jitter" on décale légèrement les points pour qu'ils soient moins supperposés et donc que l'on voie mieux la quantités d'observations au même endroit.


#violin plot = 1 variable quali, 1 variable quanti

pour chaque variable quali, on représente sa distribution par une forme sur l'axe des y (var quanti) ça ressemble à des violons.

c'est un genre d'histogramme renversé pour chaque variable.

sb.violinplot(data = 'dataframe', x = 'billy', y = 'joe')
