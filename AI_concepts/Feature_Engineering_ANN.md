# process:

1) on transforme les variables qui n'ont pas de sens propre (ex datetime) into more meaningless variables (day of week, year, ...)

2) on sépare les variables continues des variables "catégories" que l'on encode en tant que telles (one hot encoding ou embeddings qui est une version compressée des one hot encoding qui transforment les valeurs des catégories en binaires)
C'est fait avec pandas: df.dtypes ==> liste les datatypes, on veut des types category

on liste les variables de type categorie (et pas continues)
cat_cols = ['we_wd','ampm','hour']

on les transforme en type 'category' avec pandas
for cat in cat_cols:
    df[cat] = df[cat].astype('category')

on checke les datatypes avec df.dtypes

//on regarde dans chaque categorie avec
df['we_wd'].head()   ==> liste les premiers elements 


3) on transforme les arrays numpy des variables discrètes, continues et des labels (resultats) en tensors pytorch




#Feature engineerign with ANN

1) for the features to work well with a neural network, they need to have a meaning :


Datetime for exemple is difficult to exploit, better divide it in day of week, hour of day, morning or evening... 
ex of taxi fares, can have variations according to real variable not abstract ones.

look for numpy or pandas datetime dt functions that can manipulates quickly datetime variable, but first convert string to a datetime datatype.


GPS coordinates can be transformed into distances, that can be much more useful for the neural network to work well.


==> categorical data vs continuous variables.


Note: regression problem ==> we want to find the proportion / %of chance for a variable.
Categorization problem ==> we want to find the category a variable is or not


==> one hot encoding ==> transform categorical values into numbers so that the neural network can understand them

1) df.dtypes ==> we look at the datatypes of all categorical columns. We need to change them from number datatype into category datatype

cat_cols = ['we_wd','ampm','hour']

for cat in cat_cols:
    df[cat] = df[cat].astype('category')

==> on change toutes les variables de type catégorie en type category.

on visualise avec df['we_wd'].head()

df['we_wd'].cat.categories ==> retourne les catégories
df['we_wd'].cat.codes ==> retourne les codes numériques qui encodent ces catégories

wd = df['we_wd'].cat.codes.values 
hr = df['hour'].cat.codes.values
ampm = df['ampm'].cat.codes.values

==> retourne les codes en un array Numpy, ce qui est nécessaire car pour les mettre dans pytorch il faut déjà les avoir au format d'array Numpy

==> idem pour les autres variables catégories

stack different arrays together, to put them in a large matrix:

cats = np.stack([wd,hr,ampm], axis=1)  ==> we stack all this into a numpy array, with a array by colomn (axis = 1=> colonnes)

cats = torch.tensor(cats, dtype=torch.int64) 

une fois l'array numpy pret, on le transforme en tensor, en passant le dtype que l'on souhaite: torch.int64 pour les variables "categories" et torch.float pour les variables continues


===============

Rappel compréhensions de liste: boucle à travers un array en respectant une contition, le tout simplifié en une ligne

nombres = [ 121, -10, 32, -43]

ma_liste = [ nombre for nombres in nombre > 0]    ===> 

ma_liste = [ int(nombre) for nombre in nombres > 0]   ===> resultat souhaité for element in array condition.



==============

we separate 3 different tensors: categorical variables tensor, continuous variables tensor, and y ( labels )


Torch embeddings: ==> 1 hot encoding



===================



https://www.quora.com/What-does-PyTorch-Embedding-do

Comment encoder ses categorical columns:

on calcule le nombre d'embeddings que l'on a besoin = +ou- colonnes / 2  mais maxi 50


