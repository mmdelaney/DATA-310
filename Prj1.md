# Project 1

## Selected City: Boston!
![image](https://user-images.githubusercontent.com/78870884/113354107-a1e59380-930c-11eb-94f5-0732cde4feca.png)

### Data

Initially, I scraped 400 house observations Zillow.  Each observation included values for the house's listed price, address, number of bedrooms, number of bathrooms, and number of squarefeet.  One observation was missing a value for number of squarefeet, so I dropped it.

As I was investigating the descriptive statistics of my data, I noticed that one home was listed for $350.  I was doubtful that this value was correct.  When I Googled the address and saw that house was a brownstone a few blocks away from the Charles River, I decided that $350 was definitely incorrect.  I assumed there was an error in Zillow and the house was actually suppoused to be listed at $350,000, but I decided to drop that observation just to be safe.

I was also a little worried about my maximum obervation. The most expensive house in my dataset was listed at $45 million. However, when I googled this address, 1 Franklin Street, I discovered that it is Millenium Tower, a luxury apaerment building in downtown Boston. According to LuxuryBoston.com, the building's Grand Penthouse is currently for sale. This property included the entirety of the building's 60th floor and features a 360 degree balcony with views of Boston harbor, 8 bedrooms, 12 bathrooms, 7 fireplaces, a library, a movie and game area, and staff quarters. For fun, I have included some photos of this monstrosity below. 

![image](https://user-images.githubusercontent.com/78870884/113351414-dbb49b00-9308-11eb-9d0a-2cd84d6f62ff.png)


![image](https://user-images.githubusercontent.com/78870884/113351600-19b1bf00-9309-11eb-8b44-f7449050156b.png)


![image](https://user-images.githubusercontent.com/78870884/113351350-bf186300-9308-11eb-9a5f-5044a286618a.png)

Despite the absurdity of the $45 million listing and its potential to skew my model, I decided to keep the observation since it's a legitimate listing. So, after dropping the $350 house, I was left with 398 obervations. See the descriptive statistics of these observations below.

|   |Listed Price|Bedrooms|Bathrooms|Square Feet|
|---|------------|--------|---------|-----------|
|Count|398|398|398|398|
|Mean|$1,506,614|2.91|2.58|1938.51|
|Std|$3,807,347|1.49|1.84|1854.47|
|Min|$30,000|1|1|520|
|25%|$501,000|2|1|912|
|50%|$672,000|2|2|1211|
|75%|$979,750|3|3|1959.75|
|Max|$45,000,000|---|12|13,256|


### Model Description

I ended up creating two different models.  Both have the same model architecture as the model I created to analyze the Mathews housing data from Exercise 1. These are Keras sequential models with a stochastic gradient descent optimizer and a mean squared error loss function. The first model was very simple and only had 3 inputs: number of bedrooms, number of bathroom, and number of squarefeet. With these inputs, the model tried to predict the houses' listed prices. Code to create the original model can be seen below.

```
model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[3])])
model.compile(optimizer='sgd', loss='mean_squared_error')

x1 = np.array(homes['beds'], dtype = float)
x2 = np.array(homes['baths'], dtype = float)
x3 = np.array(homes['sqft_scale'], dtype = float)
xs = np.stack([x1, x2, x3], axis=1)
ys = np.array(homes['prices_scale'], dtype = float)

history = model.fit(xs, ys, epochs=500)
```

As demonstrated below, this first model did not learn very well since the loss function barely changed between the first and last epoch.

![image](https://user-images.githubusercontent.com/78870884/113357911-ca708c00-9312-11eb-9264-caad4953ea4c.png)


### Output Analysis

MSE w/ just bed, bath, and sqft:  13635133589357.477

MSE w/ zips: 8768492452983.424

### Best/Worst Deals


Orig graphs


![image](https://user-images.githubusercontent.com/78870884/113357972-eecc6880-9312-11eb-8425-ddef2d63b419.png)

Zip graphs

![image](https://user-images.githubusercontent.com/78870884/113360607-1a9e1d00-9318-11eb-9dab-44a5a78ff974.png)

![image](https://user-images.githubusercontent.com/78870884/113360640-2c7fc000-9318-11eb-8cc9-e42072bc9eb1.png)



