#how to build datasets with pytorch



#USING SCIKIT_LEARN
============================


scikit-learn is a genearal machine learning library doing a lot of statistics and machine learning alorithms support vector machines, random forests, as well as a lot of utilities for general pre- and postprocessing of data. It is not a neural network framework.


0) on prépare le dataset

==> import de csv grace à pandas

dataset = pd.read_csv('path_to_file.csv')
dataset.head()  ==> pour voir ce qu'il y a dedans

==> on découpe le dataset en deux numpy arrays "features" et "labels" (les labels sont le résultat à prédire et les features les données qui servent à l'estimation)

features = dataset.drop('label_col_name', axis=1).values  (le ".values" récupère uniquement les valeurs et donc transforme le pandas en un array numpy)
labels = dataset['label_col_name'].values    ==> on récupère uniquement la colonne 'label' du dataset.


1) on importe scikit learn:

### on importe scikit learn, plus particulièrement le module train_test_split
from sklearn.model_selection import train_test_split


2) on découpe le dataset en deux grace à la fonction train_test_split de scikit_learn

X_train, X_test, y_train, y_test = train_test_split(features, labels, test_size=0.33, random_state=33)


3) on transforme les datasets train et tests en tensors pytorch

X_train = torch.FloatTensor(X_train)
X_test = torch.FloatTensor(X_test)

the "labels" doesn't need to be float as they are 0.0 1.0 2.0...but should be really 0, 1 , 2 (integers), we cast them as integers (longs)

y_train = torch.LongTensor(y_train).reshape(-1, 1)   ==> reshape to a column form instead of having a single line array, so that it can match the shape of the X_train, X_test tensors



# using pytorch torch.utils.data  and DataLoader
===========================================================
helps preparing data into batch size to help load them into the models parts after parts. (instead of in one huge batch: very important for learning models with huge datasets)


1) import TensorDataset and DataLoader

from torch.utils.data import TensorDataset, DataLoader

prepare data to split the row of labels from the row of features.

features = df.drop('label', axis=1).values
labels = df['label'].values


### Prepare the dataset with tensordataset
dataset = TensorDataset(torch.FloatTensor(features), torch.LongTensor(labels))

### Prepare dataset_loader (cut into batches randomly shuffled)
==> from the previously prepared tensordataset.

dataset_loader = DataLoader(dataset, batch_size=50, shuffle=True)




