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

This filter makes the image significantly darker to the point where the staircase is almost unrecognizable.

### What are you functionally accomplishing as you apply the filter to your original array? 

When you apply a filter to an image, the filter's 3X3 matrix gets applied to all the original image's pixels. Each pixel is multiplied by a corresponding number within the 3X3 matrix. As a result, the filter creates a uniform alteration to the orignial image that creates an output of the same image with a unique new effect.

### Why is the application of a convolving filter to an image useful for computer vision?

I think convolving filters are useful in computer vision because images contain a number of unnecessary details that take up memory when processed through a model.  By using filters that highlight the most relevant aspects of an image, models can better pick up on the important elements of an item you're trying to get it to learn.  Also, by simplifying the image, it is also easier and faster for the model to process.

### Another useful method is pooling. Apply a 2x2 filter to one of your convolved images, and plot the result. 

![image](https://user-images.githubusercontent.com/78870884/110268322-77175200-7f8f-11eb-82dc-0c3c82b5cc34.png)

### In effect what have you accomplished by applying this filter? 

By applying the 2X2 filter, the image looks very similar to the original, but is slightly less focused. The pooling maintains the identifiable features of the orginial image, but the resulting image is a simplified version of the original.

### Does there seem to be a logic (i.e. maximizing, averaging or minimizing values?) associated with the pooling filter provided in the example exercise (convolutions & pooling)? 

The pooling feature seems to maximize input pixel values. When the pooling filter is applied to a 2x2 block of pixels, the output keeps the largest pixel values and removes the 3 remaining smaller pixels. 

### Did the resulting image increase in size or decrease? Why would this method be useful?

The resulting image decreased in size.  The original image was 512X512, and the resulting image was 256X256.  This method will be useful because it maintains the features of the original image so the computer could still train to recognize the depicted object, but since the image is smaller, it can process more quickly and efficiently.

### Convolve the 3x3 filter over the 9x9 matrix and provide the resulting matrix.

![image](https://user-images.githubusercontent.com/78870884/112526114-fa022000-8d77-11eb-991d-ba731a3c5e92.png)

Resulting Matrix:
'''
0 0 0 3 0 0 0
0 0 0 3 0 0 0
1 1 1 3 1 1 1
1 1 1 3 1 1 1
1 1 1 3 1 1 1
0 0 0 3 0 0 0
0 0 0 3 0 0 0
'''
