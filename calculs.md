Integral => aire en dessous d'une fonction.

note Pi = ratio circonférence du cercle sur son diamètre

on peut voir la surface d'un disque comme la somme de petits cercles de rayons concentriques.
Si l'on déroule la circonférence de ces cercles du plus petit au plus grand, ils s'alignent en dessous d'une droite d'équation 2PiR, Et la surface correspond à celle du triangle rectangle.


Intégrale =  surface sous une courbe:
Dérivée =  angle de croissance ou décroissance de la courbe
==> how sensitive  a function is to a small change in its input


dA/dx = f(x) pour dx très petit

dA/dx ==> dérivée

la variation de surface sous la courbe / la variation de x ==> la variation de la hauteur sous la courbe (f(x)

Dérivées sont la clé pour trouver les intégrales (aires en dessous d'une courbe)

La dérivée d'une fonction en dessous un graphe donne la fonction qui définie le graphe (la courbe) lui même.

# dérivées:

Hauteur de la courbe: distance totale parcourue par la voiture jusqu'à ce moment dans le temps

instantaneous rate of change: we calculate it by dividing 
dS(small increase in distance/ dt (small increase in time), this is a function of t, as this value change for each value of t (axe des abscisses)

slope of the line tangeant to the curve at a single point

pour trouver la dérivée d'une fonction:

imaginer la surface ou le volume d'une fonction:

ex : f(x) = x³ ==> volume d'un cube

si l'on augmente le cube d'une valeur dx (approchant 0), le volume incrémental du cube est de x³, la valeur incrémentale correspond à la surface de ses 3 faces ==> 3x²

d(x^n)/dx = n * x^(n-1) ==> power rule:  d(x⁵)/dx = 5x⁴


==> Trig: cercle de rayon 1.

Lorsque l'on fait bouger le rayon autour du cercle d'un certain angle, le sinus de cet angle est la hauteur du point sur le cercle (hauteur parallèle a l'axe des y).

Le cosinus est la variagion de la projection de la longueur du point sur l'axe des x.

cos(0deg) = 1 ==> car projection sur l'axe des x, l'angle nul correspond a la plus grande distance = rayon = 1
sin(90)  = 1 ==> car projection sur l'axe des y vertical


la dérivée du sinus (qui passe par 0) est le cosinus.
dérivée du cosinus = - sin(x)

## Derivative chain rule

sum product and composition (sin(x²))

### dérivée d'une somme = somme des dérivées de chaque fonction
 
In math, to understand products concepts, it's interesting to compare it to areas
ex : on prend un carré avec comme côté chacune des deux fonctions de x a multiplier.
==> on ajoute une mini part de chacun des côtés, et on regarde son impact sur l'aire globale.
==> la mini surface ajoutée à chaque côté => la longueur du côté (fonction num1) x la largeur (dx)
==> idem pour le second côté avec la deuxième fonction.

On a donc la dérivée de la surface (= produit des deux côtés) ==>


### dérivée d'un produit "left d right, right d left"
d/dx (sin(x)*x²) => sin(x)*2x + x²cos(x)

"left d right, right d left"


### dérivée d'une fonction multipliée par une constante = constante * dérivée

### dérivée d'une fonction composée:

d/dx(g(h(x)) = d(g)/dh (h(x)) * d(h)/dx(x)

d(sin(x²)) ==> cos(x²) * 2x*dx

dérivée d'une fonction composée = dérivée de la fonction externe en prenant la fonction interne originale, multiplié par la dérivée de la fonction interne.

On commence par évaluer la dérivée par rapport à la fonction la plus extérieure, on considère la dérivée par rapport a une mini augmentation de la fonction intérieure, puis, si on cherche à l'exprimée par rapport à x, on et non par rapport à la fonction intérieure, on doit la multiplier par la dérivée de le fonction intérieure, et ainsi de suite jusqu'à arriver à x, pour avoir la dérivée par rapport à x et non par rapport à la fonction intérieure.

## dérivée d'une exponentiel

quand on ajoute deux valeurs dans l'exponentiel, celà revient a faire le produit de ces exponentiels
2⁽²⁺y⁾ = 2²*2^y

la dérivée d'un exponentiel (2^t ==> 2^t* constante 

le ratio de croissance de l'exponentiel sur une très petite augementation est directement proportionnel à l'exponentiel mais avec une constante qui varie selon la veleur de l'exponentiel

Il y a une valeur d'exponentiel pour laquel la dérivée est directement égale à sa dérivée :
e ==> la valeur 2,718
==> e^t = d(e^t)/dt

d(e ^ct)/dt = cst * e^ct


e^t = e^ln(2)t

e^ct => exponentiel de e x constante ==> chain rule ==> e^ct x c


Natural log ==> e^? = 2 

e^ln(2) = 2

e^(?) = 5 ==> ln(5)

en math on voit rarement une autre base que "e", e^ct (avec c une constante) permet de faciliter les calculs (avec le ln qui répond à la question e^combien = 2

mais c'est la même chose d'écrire 2^t ou e^ln(2)t


e ==> 2,718 est la constante spéciale qui donne d(e^t)/dt = e^t  ==> l'exponentiel de cette constante est égale à sa dérivée

plutot que d'utiliser n'importe quelle autre base pour l'exponentiel, on cherchera a convertir le nombre en une exponentielle de base e, plus facile à dériver avec la règle des chaines: en effet:

e^7x  = e^7x * 7  (dérivée de la fonction externe ==> dans ce cas toute la fonction car avec "e" la fonction est égale à sa dérivée, multipliée par la dérivée de la fonction interne (d(7x) => 7)


2^t = e^ln(2)*t ==> derivee ==> ln(2)* e^ln(2)*t

ln(base) log(e)

Une constante = e^ln(constante) ==> ex: 7 = e^(ln7)   car le ln détermine quelle est l'exposant qui donne la valeur prévue. ln est l'inverse de l'exponentiel.
logarithme naturel de base e car ln(e) = 1


## pythagore:

Hypothenuse au carré = coté 1 au carré +  cote 2 au carré



