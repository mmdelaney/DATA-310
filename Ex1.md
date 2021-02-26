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

Based on this model,  

Church st house - 4 beds - $399,000
Hudgins house - 3 bed - $97,000
Mathews house - 5 bed - $347,500
Mobjack house - 4 bed - $289,000
Moon house - 2 bed - $250,000
New Point Comfort - 3 bed - $229,000
