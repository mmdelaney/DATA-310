# Exercise 1

### In Laurence Maroney’s video, What is ML, he compares traditional programming with machine learning and argues that the main difference between the two is a reorientation of the rules, data and answers. According to Maroney, what is the difference between traditional programming and machine learning?

Maroney explains that in traditional programming, programmers write code that outlines a set of rules that are followed but input data in order to output answers to a problem.  Machine Learning is a reorientation of this classic model.  In Machine Learning, instead of figuring out the rules to answer a problem, programmers input large amounts of data and answers so that a machine can figure out the correct set of rules.  For example, Maroney uses the example of training a smartwatch to recognize unique activities like walking, running, and biking by having individuals wear a smartwatch and identify the correct label of their activity so that the machine can learn the patterns of each activity in order to predict them in the future.  

### With the first basic script that Maroney used to predict a value output from the model he estimated (he initially started with 10 that predicted ~31. Modify the predict function to produce the output for the value 7. Do this twice and provide both answers. Are they the same? Are they different? Why is this so?

When I change the predict function to output for the value of 7, the output was 22.00301.  When I re-run the model and predict the output value of 7 again, the output was 22.000021.  Even though both of these values are extremely close to 22, they are slightly different.  This is because neural networks are structures to make predictions based on probabilities since there are no set parameters, like in traditional programming.  Therefore, since we can only teach our models based on a limited amount of data, this leaves open the possibility for the model to interpret the data slightly differently each time.

### Using the script you produced to predict housing price, take the provided six houses from Mathews, Virginia and train a neural net model that estimates the relationship between them. Based on this model, which of the six homes present a good deal? Which one is the worst deal? Justify your answer.

```
model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[1])])
model.compile(optimizer='sgd', loss='mean_squared_error')
xs = np.array([4.0, 3.0, 5.0, 4.0, 2.0, 3.0], dtype=float)
ys = np.array([399.0, 97.0, 347.5, 289.0, 250.0, 229.0], dtype=float)
model.fit(xs, ys, epochs=1000)
```

I created this model to predict the housing prices based on the house's number of bedrooms. The results are listed in the table below.  

|House|# of Bedrooms|Listed Price|Model-Predicted Price|Price Difference|Good/Bad Deal?|
|-----|-------------|------------|---------------------|----------------|--------------|
|Church St.|4|$399,000|$299,104|+$99,896|Bad!|
|Hudgins|3|$97,000|$236,602|-$139,602|Good!|
|Mathews|5|$347,500|$361,606|-$14,106|Fair|
|Mobjack|4|$289,000|$299,104|-$10,104|Fair|
|Moon|2|$250,000|$174,099|+$75,901|Bad!|
|New Point Comfort|3|$229,000|$236,602|-$7,602|Fair|


Based on this model, the Hudgins house is by far the best deal since it is listed at almost $140,000 less than the model predicted.  The worst deal is the Church St. house since it is listed at almost $100,000 over the model's predicted price.  The Moon house is also not a great deal since it is listed at $75,000 over its predicted price.  The remaining houses are all listed at slightly under the prices predicted by the model, so I am considering these fair deals.

### UPDATE: Using the script you produced to predict housing price, take the provided six houses from Mathews, Virginia and train a neural net model that estimates the relationship between them. Based on this model, which of the six homes present a good deal? Which one is the worst deal? Justify your answer.

To improve my model, I updated it to include number of bedrooms, number of bathrooms, and squarefeet. The updated code and the new results are listed below.

```
model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[3])])

model.compile(optimizer='sgd', loss='mean_squared_error')

x1 = np.array([3.0, 1.0, 2.0, 2.0, 1.0, 2.0], dtype=float) #baths
x2 = np.array([4.0, 3.0, 5.0, 4.0, 2.0, 3.0], dtype=float) #beds
x3 = np.array([3.99, 0.97, 3.475, 2.89, 2.50, 2.29], dtype=float) #sqft

xs = np.stack([x1, x2, x3], axis = 1)
ys = np.array([3.99, 0.970, 3.475, 2.890, 2.50, 2.290], dtype=float)

model.fit(xs, ys, epochs=1000)
```

|House|# of Bedrooms|# of Bathrooms|# Sqft|Listed Price|Model-Predicted Price|Price Difference|Good/Bad Deal?|
|-----|-------------|--------------|------|------------|---------------------|----------------|--------------|
|Church St.|4|3|3,680|$399,000|$389,905|+9,095|Fair|
|Hudgins|3|1|1,238|$97,000|$163,856|-$66,856|Good!|
|Mathews|5|2|3,051|$347,500|$305,554|+$41,946|Bad!|
|Mobjack|4|2|3,524|$289,000|$307,888|-$18,888|Fair|
|Moon|2|1|1,479|$250,000|$160,028|+$89,972|Bad!|
|New Point Comfort|3|2|2,840|$229,000|$279,494|-$50,494|Good!|



