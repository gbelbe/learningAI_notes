# class

## object, instance of a class
encapsulation - one of the fundamental ideas behind object-oriented programming is called encapsulation: you can combine functions and data all into a single entity (a class) Encapsulation allows you to hide implementation details of a particular subject.


class Class_name:  ==> convention class name start with a maj. this is a constructor method.
    def __init__(self, shirt_color, shirt_size):   
        self.color = shirt_color
        self.size = shirt_size

we should not change the value of an attribute directly by accessing it like:
shirt.color = "red"


## Magic method:
override default python behavior

def __add__(self, other):

override the python + sign
init function is a magic method.

for ex: i want to add two objects to produce a third objects that corresponds to the sum.

## Inheritance:

a class can inherit methods and attributes from another class by passing this parent class 

class Shirt(Clothing):
    define a class named Shirt that inherits attributes and methods from the class Clothing


class Shirt(Clothing):
    
    def __init__(self, color, size, style, price, long_or_short):
    
        Clothing.__init__(self, color, size, price) ==> get the attributes from the Clothing class
        self.long_or_short = long_or_short ==> add a new attribute
    
    #add a specific method to Shirt class
    def double_price(self):
        self.price = 2*self.price

    #we can override a parent method by creating one with the same name as the parent



=====

# project:
  
## determine the best classification algorithm to find out if the image is a dog or not a dog
    the one that gives a good result most of the times

## determines how well the algorithm is working (% of success)

## time how long it takes to solve the classification method

Convolutional Neural Net trained with ImageNet dataset.
3 different architectures of CNN: AlexNet, VGG and ResNet


==> classifier_function in classifier.py
==> test_classifier.py exemple program to show how to use it

Great Pyrenees / Kuvasz
German Shepherd / Malinois
Beagle / Walker Hound

1) edit check_images.py

create functions to achieve the objectives



Program Outline

    Time your program
        Use Time Module to compute program runtime
    Get program Inputs from the user
        Use command line arguments to get user inputs
    Create Pet Images Labels
        Use the pet images filenames to create labels
        Store the pet image labels in a data structure (e.g. dictionary)
    Create Classifier Labels and Compare Labels
        Use the Classifier function to classify the images and create the classifier labels
        Compare Classifier Labels to Pet Image Labels
        Store Pet Labels, Classifier Labels, and their comparison in a complex data structure (e.g. dictionary of lists)
    Classifying Labels as "Dogs" or "Not Dogs"
        Classify all Labels as "Dogs" or "Not Dogs" using dognames.txt file
        Store new classifications in the complex data structure (e.g. dictionary of lists)
    Calculate the Results
        Use Labels and their classifications to determine how well the algorithm worked on classifying images
    Print the Results

You will need to repeat these tasks for each of the three image classification algorithms that are provided to you



