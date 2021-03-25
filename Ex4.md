# Exercise 4: Matrix Convolutions & Mean Squared Error 

## Convolutions

### Matrix Activity

![unnamed](https://user-images.githubusercontent.com/78870884/110256208-a1ecb080-7f65-11eb-8429-276902a097ab.jpg)

### What is the purpose of using a 3x3 filter to convolve across a 2D image matrix?

The purpose of using a 3x3 filter to colvolve across a 2D image matrix is to highlight certain features of an image to make the objects more identifiable (such as horizontal or vertical lines). This makes it easier to train computer vision machine learning models.

### Why would we include more than one filter? How many filters did you assign as part of your architecture when training a model to learn images of numbers from the mnist dataset?

We could include more than one filter to highlight more than one feature. For example, if we wanted to train a model to identify trees, it would be emphasize vertical lines that could be a trunk as well as horizontal lines that could be branches.  When training the model with the images from the mnist dataset, I think I only used one filter.  

## MSE

### From your 400+ observations of homes for sale, calculate the MSE for the following.

#### *The 10 biggest over-predictions*
#### *The 10 biggest under-predictions*
#### *The 10 most accurate results (use absolute value)*
#### *In which percentile do the 10 most accurate predictions reside? Did your model trend towards over or under predicting home values?*
#### *Which feature appears to be the most significant predictor in the above cases?*
#### *Stretch goal: calculate the MAE and compare with your MSE results*
  
