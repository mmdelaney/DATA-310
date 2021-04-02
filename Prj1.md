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
|Max|$45,000,000|9|12|13,256|


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

So, I created a second model that included a spacial variable: zipcode. To use zipcode as an input into my model, I had to create 29 separate new binary input variables that captured the 29 different zipcodes in my data. The code I used to create this second model is below.

```
model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[32])])
model.compile(optimizer='sgd', loss='mean_squared_error')

x1 = np.array(homes['beds'], dtype = float)
x2 = np.array(homes['baths'], dtype = float)
x3 = np.array(homes['sqft_scale'], dtype = float)
x4 = np.array(homes['zip1'], dtype = float)
x5 = np.array(homes['zip2'], dtype = float)
x6 = np.array(homes['zip3'], dtype = float)
x7 = np.array(homes['zip4'], dtype = float)
x8 = np.array(homes['zip5'], dtype = float)
x9 = np.array(homes['zip6'], dtype = float)
x10 = np.array(homes['zip7'], dtype = float)
x11 = np.array(homes['zip8'], dtype = float)
x12 = np.array(homes['zip9'], dtype = float)
x13 = np.array(homes['zip10'], dtype = float)
x14 = np.array(homes['zip11'], dtype = float)
x15 = np.array(homes['zip12'], dtype = float)
x16 = np.array(homes['zip13'], dtype = float)
x17 = np.array(homes['zip14'], dtype = float)
x18 = np.array(homes['zip15'], dtype = float)
x19 = np.array(homes['zip16'], dtype = float)
x20 = np.array(homes['zip17'], dtype = float)
x21 = np.array(homes['zip18'], dtype = float)
x22 = np.array(homes['zip19'], dtype = float)
x23 = np.array(homes['zip20'], dtype = float)
x24 = np.array(homes['zip21'], dtype = float)
x25 = np.array(homes['zip22'], dtype = float)
x26 = np.array(homes['zip23'], dtype = float)
x27 = np.array(homes['zip24'], dtype = float)
x28 = np.array(homes['zip25'], dtype = float)
x29 = np.array(homes['zip26'], dtype = float)
x30 = np.array(homes['zip27'], dtype = float)
x31 = np.array(homes['zip28'], dtype = float)
x32 = np.array(homes['zip29'], dtype = float)

xs = np.stack([x1, x2, x3, x4, x5, x6, x7, x8, x9, x10, x11, x12, x13, x14, x15, x16, x17, x18, x19, x20, x21, x22, x23, x24, x25, x26, x27, x28, x29, x30, x31, x32], axis=1)
ys = np.array(homes['prices_scale'], dtype = float)

history = model.fit(xs, ys, epochs=500)
```

Despite the tediousness of creating a model with 32 different variables, adding the zipcode inputs significantly improved the quality of my model. As you can see below, the adding the zipcodes helped the model learn and improve in a way it was unable to do in the original model.


![image](https://user-images.githubusercontent.com/78870884/113360607-1a9e1d00-9318-11eb-9dab-44a5a78ff974.png)


### Output Analysis

Neither of my two models were very accurate. However, my second model that included zipcodes as inputs was more accurate than the first, more simple, model.  As you can see below, the first model did a pretty poor job of predicting listed price and pretty consistently over-predicted the actual price. This model's MSE was 13635133589357.477.

![image](https://user-images.githubusercontent.com/78870884/113357972-eecc6880-9312-11eb-8425-ddef2d63b419.png)

The second model was nowhere near perfect, but adding zipcodes as inputs did somewhat improve the model's accuracy. This second model also had a smaller MSE than the first: 8768492452983.424 as opposed to 13635133589357.477.   


![image](https://user-images.githubusercontent.com/78870884/113360640-2c7fc000-9318-11eb-8cc9-e42072bc9eb1.png)

### Best/Worst Deals

With these models, the "best deals" are for houses whose listed price falls below the model-predicted prices. Therefore, the best deals are those that fall in the upper-left quadrants of the graphs above. The "worst deals" are the houses whose listed price is higher than the model-predicted price. These houses are in the lower-right quadrant of the graphs.

Best Deals:

|Address|Actual Price|Preidcted Price|Difference|
|---|------------|--------|---------|-----------|
|99-105 Broad St #2F, Boston, MA 02110|649000|398|398|398
|66 Chestnut St #11, Boston, MA 02108|1425000|2.91|2.58|1938.51|
|65 E India Row APT 27, Boston, MA 02110|3199000|1.49|1.84|1854.47|
|37 Branch St, Boston, MA 02108|4995000|1|1|520|
|377 Commonwealth Ave #6, Boston, MA 02115|549000|2|1|912|
|342 Commonwealth Ave APT 2, Boston, MA 02115|539000|2|2|1211|
|456 Beacon St APT 4, Boston, MA 02115|750000|3|3|1959.75|
|7 Albemarle St APT 1, Boston, MA 02115|647000|9|12|13,256|
|362 Commonwealth Ave APT 2D, Boston, MA 02115|625000$45,000,000|9|12|13,256|
|103 Gainsborough St APT 103, Boston, MA 02115|885800|9|12|13,256|

Worst Deals:

|   |Listed Price|Bedrooms|Bathrooms|Square Feet|
|---|------------|--------|---------|-----------|
|Count|398|398|398|398|
|Mean|$1,506,614|2.91|2.58|1938.51|
|Std|$3,807,347|1.49|1.84|1854.47|
|Min|$30,000|1|1|520|
|25%|$501,000|2|1|912|
|50%|$672,000|2|2|1211|
|75%|$979,750|3|3|1959.75|
|Max|$45,000,000|9|12|13,256|


