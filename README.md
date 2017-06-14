# Observations

## Dataset
MNIST is too simple in terms of pattern that there is no significant change in determining the factors contributing to the prediction when number of sampling increases. Thus, for this kind of dataset, 1000 samplings per prediction is adequate.
sa
## Experiment
With aforementioned dataset, number of iterations (the number of times do backpropagation) is 2000 for every model. I found this number is enough to reach an accuracy ![equation](https://latex.codecogs.com/gif.latex?\geq&space;90).
### Model 1: Neural Network with no hidden layer
- Architecture: input layer -> softmax -> output layer
- The plot of weight seems randomly uniform, there is no clear patter suggests a correlation to any digits from 0 to 9. 
![Alt text](img/model1_weight.png?raw=true "Optional Title")
- 
TODO LIST:
