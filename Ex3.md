# Exercise 3

### Last time you did an exercise (convolutions and pooling) where you manually applied a 3x3 array as a filter to an image of two people ascending an outdoor staircase. Modify the existing filter and if needed the associated weight in order to apply your new filters to the image 3 times. Plot each result, upload them to your response, and describe how each filter transformed the existing image as it convolved through the original array and reduced the object size. 

**Original Staircase Image:**

![image](https://user-images.githubusercontent.com/78870884/110259517-10396f00-7f76-11eb-811d-510249b678b1.png)

**Filter 1:**
```
filter1 = [ [-1, -1, -1], [0, 0, -1], [-1, 2, -1]]
```
![image](https://user-images.githubusercontent.com/78870884/110259770-64911e80-7f77-11eb-9e83-6e359792c02f.png)

This filter seems to create greater contrast in the image by brightening the lighter parts of the image and making the dark lines more distinct.

**Filter 2:**
```
filter2 = [ [0, 1, 0], [0, -1, 0], [1, 1, -1]]
```
![image](https://user-images.githubusercontent.com/78870884/110259901-fa2cae00-7f77-11eb-9b6f-1ea92b627e83.png)

This filter makes the image seem more blurry by making the lines less definied.

**Filter 3:**
```
filter3 =[ [2, -2, 1], [1, -1, -2], [0, 0, 0]]
```

![image](https://user-images.githubusercontent.com/78870884/110259982-614a6280-7f78-11eb-9149-53fc494f68a5.png)

This filter makes the images significantly darker to the point where the staircase is almost unrecognizable.

### What are you functionally accomplishing as you apply the filter to your original array? 

When you apply a filter to an image, the filter's 3X3 matrix gets applied to all the original image's pixels. Each pixels is multiplied by a corresponding number within the 3X3 matrix

### Why is the application of a convolving filter to an image useful for computer vision?

I think convolving filters are useful in computer vision because images contain a number of unnecessary details that take up memory when processed through a model.  By using filters that highlight the most relevant aspects of an image, models can better pick up on the important elements of an item you're trying to get it to learn.  Also, by simplifying the image, it is also easier and faster for the model to process.

### Another useful method is pooling. Apply a 2x2 filter to one of your convolved images, and plot the result. In effect what have you accomplished by applying this filter? Does there seem to be a logic (i.e. maximizing, averaging or minimizing values?) associated with the pooling filter provided in the example exercise (convolutions & pooling)? Did the resulting image increase in size or decrease? Why would this method be useful? Stretch goal: again, instead of using misc.ascent(), apply the pooling filter to one of your transformed images.

### Convolve the 3x3 filter over the 9x9 matrix and provide the resulting matrix.
