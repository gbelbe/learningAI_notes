#ANN with pytorch

to create a model with pytorch we need to create a model class, inheriting the nn.Module class


class Model(nn.Module):
    def __init__(self, in_features=4, h1=8, h2=9, out_features=3):

    #here we create the different layers of the model.
    # 4 features passed to the model (dimensions of the petals) + 2 hidden layers of 8 and 9 neurons, and one output layers of 3 classes

    # generally we have at least as many neurons in the hidden layers as there is input features


Once we tested the model against the test data, we can save it into a separate file:

torch.save(model.state.dict(),'my_iris_model.pt')

    State dictionary is the saved parameters of the model
