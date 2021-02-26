
# Exercise 2

### In the video, First steps in computer vision, Laurence Maroney introduces us to the Fashion MNIST data set and using it to train a neural network in order to teach a computer “how to see.” One of the first steps towards this goal is splitting the data into two groups, a set of training images and training labels and then also a set of test images and test labels. Why is this done? What is the purpose of splitting the data into a training set and a test set?

The data is subset into training and testing groups so that the model can learn on one set of data and get tested on another. The model uses the training set to learn which labels are attached to which images. Then, we use the test set to see how accurately the model can identify the images. The data in the testing group must be unique from that in the training group because the model has already learned the images in the training group, so it must be tested on new data. 

### The fashion MNIST example has increased the number of layers in our neural network from 1 in the past example, now to 3. The last two are .Dense layers that have activation arguments using the relu and softmax functions. What is the purpose of each of these functions. Also, why are there 10 neurons in the third and last layer in the neural network.

The relu function ensures that outputs that are less than 0 get changed to 0 so that negative numbers do not skew the results. The softmax function helps identify the most likely label, or what clothing item an image most likely depicts. Each of the 10 neurons will calculate the probability that a an images matches its unique label, and softmax simplifies the process by setting the largest probability to 1 and the rest of the probablities to 0.

There are 10 neurons in the last layer of the neural network because there are 10 different types of clothing items in the data set.  Therefore, each individual neuron calculates the probability that a particular images matches its specific clothing type.


### In the past example we used the optimizer and loss function, while in this one we are using the function adam in the optimizer argument and sparse_categorical- crossentropy for the loss argument. How do the optimizer and loss functions operate to produce model parameters (estimates) within the model.compile() function?

?????

### Using the mnist drawings dataset (the dataset with the hand written numbers with corresponding labels) answer the following questions: What is the shape of the images training set (how many and the dimension of each)?  What is the length of the labels training set?  What is the shape of the images test set?  Estimate a probability model and apply it to the test set in order to produce the array of probabilities that a randomly selected image is each of the possible numeric outcomes (look towards the end of the basic image classification exercises for how to do this — you can apply the same method applied to the Fashion MNIST dataset but now apply it to the hand written letters MNIST dataset).

* The images training set is made up of 60,000 28x28 images
* The label trainging set is 60,000 labels long
* The images test set is made up of 10,000 28x28 images
* 

### Use np.argmax() with your predictions object to return the numeral with the highest probability from the test labels dataset.

### Produce a plot of your selected image and the accompanying histogram that illustrates the probability of that image being the selected number
