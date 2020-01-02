Pandas is a library on top of Numpy. It can hold multiple types of values unlike numpy.

Panda has series and data frames.


#Panda Series

in Series we can assign labels for each element and we can have elements of different data type



import pandas as pd

groceries = pd.Series(data=[3, 4, "yes"], index=["carottes", "patates", "milk"])

groceries.shape
(3,)  ==> trois colonnes une ligne

groceries.ndim ==> numbers of dimensions of the array
groceries.size ==> numbers of elements


We can print all indices by typing :
groceries.index; 

List data only : 

groceries.values

and check if an index is in the serie:  'cake' in groceries  ==> return true or false


## Retrieving Panda Series elements

groceries['milk']
access to a specific value providing an index label

groceries[['milk', 'chocolate']] more than one label

groceries[0] (by index number) first index
groceries[-1]  ==> last item (going backwards)
groceries[[0, 1]] multiple items

to desambiguate:

groceries.loc['milk'] ==> loc = index label
groceries.iloc[2] ==> int index

panda series is mutable ==> we can change its elements after it has been created as in numpy


groceries.drop('gateau', inplace=True)


## Operations

import pandas as pd
import numpy as np

groceries = pd.Series([1, 3, 4], ['carottes', 'navets', 'endives'])

np.sqrt(groceries)

## boolean selection

if we want to select all elements values that fits a certain condition

dist = pd.Series([10,100,1000], ['lille', 'paris', 'marseille'])

shortest_dist = dist[dist<1000]





#Pandas DataFrames

===> 2 dimensional arrays with named rows and columns, like an excel file

We can create a DataFrame from several panda Series, chained as a dictionnary, (or we can create a df from various arrays of the same size chained as a dict)

items = { 'Bob': pd.Series([10, 20, 30], ['bike', 'pants', 'watches']), 'Alice': pd.Series([20, 30, 40]....)

items is a dictionnary of various pandas Series.
Cols of the dataframe are taken by the keys of the dictionnary

we can pass it to a FataFrame ==> 

shopping_carts = pd.DataFrame(items)

if we have created the df from a dict of arrays, we can add labels while creating the df ==> pd.DataFrame(dict_data, index=['label1', 'label2'...


DataFrame merge the series in the dict into a spreadsheet. Where some rows haven't any value, it places a "NaN" value that needs to be removed before calculations

## getting infos from a DataFrame


shopping_carts.values ==> gets the arrays of values only
shopping_carts.shape (5rows 2 columns
shopping_carts.ndim (2 dimensions)
.size... ==> 2x5 = 10 = total size


## loading parts of the dict in a DataFrame

only bob col

sel_shop_cart = pd.DataFrame(items, columns=['Bob'])

only 2 elements from both cols

sel_shop_cart = pd.DataFrame(items, index=['pants', 'books])



## accessing elements of a dataframe

column, and then row, always in this order.

dataframe['col']['row']

**with a condition**

dataframe[(dataframe > 5).any(axis=1)]
==> shows a dataframe values of True or False that replies to the conditions of the elements with value > 5
==> reduce the selection only to the rows that have a value like this



## Adding rows and columns

### col

adding a new column ==> dataframe['new_col'] = [10, 32, np.nan]  ==> new column new_col is created with values 10, 32, NaN

adding a new column from an operation on other cols:  ==> dataframe['newcol'] = dataframe['col1'] + dataframe['col2']

### row

we have to create a new DataFrame with the row information, then append it to the former

1) create a dict 
new_row = {'Bob': [10,20,30], 'Joe': [20,10,22]}

2) create a new df 
new_data_frame = pd.DataFrame(new_row, index='Store 5')  ==> index = name of the row to be added

3) append this dataframe to the old one 
store_items = store_items.append(new_data_frame)



## fill NaN values

to prepare a dataframe before working with a machine learning project, you need to fill in the blanks or removes these blanks.

* 1st : count the nans
--------------------

x = my_data_frame.isnull().sum().sum()

=> transform all data into True or False ==> true == to 1 
=> sum each columns (True =1 and False=0)
=> sum all sums columns to get the full total.

or we can count the values without NaN 

my_data_frame.count().sum()

count all non null values of each cols, then sum this number for all columns

* delete rows or cols with Nan values
-------------------------------------

axis = 0 ==> rows
axis = 1 ==> cols

my_data_frame.dropna(axis=0 inplace=True) ==> eliminate any row with nan value
my_data_frame.dropna(axis=1 inplace=True) ==> idem with cols

if inplace=True, modify to the same DataFrame, if not, then only applied to a new one

my_data_frame.dropna(axis=0)


* fill na values
----------------
**fillna(method, axis=, inplace=)**

my_data_frame.fillna(0) ==> fill all NaN values with 0

**forward filling** ==> fills the NaN value with the value of the previous value along the specified axis

my_data_frame.fillna(method='ffill', axis=0)  ==> will fill in the missing values of each row according to the same value of the previous row

except for the first row that hasn't any previous value, we can also use axis=1 it will use the value of the previous column

**method='backfill'**, is the same but filling the missing value with the next existing value

==> be careful to set inplace=True if we want to modify the working dataframe

**method='linear'** linear interpolation of the NaN between the last and next one  (moyenne)

if we want to fill the value of the NaN with the average value of the column

data_frame.fillna(data_frame.mean())


## import from CSV

df = pd.read_csv('file.csv')

display first rows:

df.head()

ex:
google_stock =  pd.read_csv('./GOOG.csv', usecols=['Adj Close', 'Date'], index_col='Date', parse_dates=['Date'])

select only some cols, convert date from text to date...
google_stock.head() ==> print the first 5 lines to check

rename column in a dataframe: google_stock = google_stock.rename({'col_name':'Google'}, axis=1)

dataframe.mean()
dataframe.std()
dataframe.corr()==> corrélation des variables entre elles
