# Observations

## Dataset
MNIST is too simple in terms of pattern (images of digit from 0 to 9) that there is no significant change in determining the factors contributing to the prediction when number of sampling in LIME increases. Thus, for this kind of dataset, 1000 samplings per prediction is adequate.
![Alt text](http://theanets.readthedocs.io/en/stable/_images/mnist-digits-small.png)

## LIME
Local Interpretable Model-agnostic Explanation is a model trying to interprete the result of any complex machine learning technique in a comprehensive manner such that end-users (non-expert) can understand by themselves. Previous approaches try to capture how input influences prediction by observing over all data points. However, this model believed that in order to truly interprete the decision making process, each data point is unique and has its own reasoning which can not be made to be general for other similar (different in one feature, for instance) data points.  
Imagine the representation of true distribution of data points is extremely complex and curved. Let's take a magnifier and zoom in a particular point. Now you can find at least one straight line to divide the feature space (limited by the visionary zone of magnifier) into two sets: positive and negative points. This is the core notion of LIME, and by sampling datapoints nearby by disturbing features with a predefined distribution, one could gain enough data to train a simple classifier (decision tree for instance), and thus can explain the output of prediction. 

## Experiment
With aforementioned dataset, number of iterations (the number of times to do backpropagation) is 2000 for every model. I found this number is enough to reach an accuracy ![equation](https://latex.codecogs.com/gif.latex?\geq&space;90) for every model.
### Model 1: Neural Network with no hidden layer
- Architecture: (input layer \* weight) -> softmax -> output layer
- The plot of weight seems to be randomly uniform, there is no clear patter suggests a correlation to any digits from 0 to 9. 
![Alt text](img/model1_weight.png?raw=true)

It is no doubt that the image after being processed via this filter (weight) would be saturated into random as well, hence my guess for its yet powerful prediction is the difference in mean of weight set for each digit. The weights in below image are different from each other because they were retrained, however the color bandwidth show similar color distribution. Which leads to the conclusion that they make prediction by training the mean weight to be in some particular range of value. 
![Alt text](img/model1_sample.png?raw=true) 

### Model 2: Neural Network with 1 hidden layer
- Architecture: (input layer \* weight) -> sigmoid -> (hidden layer * weight)-> softmax -> output layer
- Similar observations were made and randomness exists in trained weight. The only difference is a new weight set and layer were added into previous model. Below is image shows  

![Alt_text](img/weight_img_model2.png?raw=true "Weight and Image")

TODO LIST:
