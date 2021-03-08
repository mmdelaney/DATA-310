# Exercise 3

### Last time you did an exercise (convolutions and pooling) where you manually applied a 3x3 array as a filter to an image of two people ascending an outdoor staircase. Modify the existing filter and if needed the associated weight in order to apply your new filters to the image 3 times. Plot each result, upload them to your response, and describe how each filter transformed the existing image as it convolved through the original array and reduced the object size. 

Original Staircase Image:

![image](https://user-images.githubusercontent.com/78870884/110259517-10396f00-7f76-11eb-811d-510249b678b1.png)

Filter 1:
```
filter1 = [ [-1, -1, -1], [0, 0, -1], [-1, 2, -1]]
```
![image](https://user-images.githubusercontent.com/78870884/110259770-64911e80-7f77-11eb-9e83-6e359792c02f.png)

Filter 2:
```

```


### What are you functionally accomplishing as you apply the filter to your original array (see the following snippet for reference)? Why is the application of a convolving filter to an image useful for computer vision? Stretch goal: instead of using the misc.ascent() image from scipy, can you apply three filters and weights to your own selected image? Again describe the results.



### Another useful method is pooling. Apply a 2x2 filter to one of your convolved images, and plot the result. In effect what have you accomplished by applying this filter? Does there seem to be a logic (i.e. maximizing, averaging or minimizing values?) associated with the pooling filter provided in the example exercise (convolutions & pooling)? Did the resulting image increase in size or decrease? Why would this method be useful? Stretch goal: again, instead of using misc.ascent(), apply the pooling filter to one of your transformed images.

### Convolve the 3x3 filter over the 9x9 matrix and provide the resulting matrix.
