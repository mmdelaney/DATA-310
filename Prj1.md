# Project 1

## Selected City: Boston!
![image](https://user-images.githubusercontent.com/78870884/113354107-a1e59380-930c-11eb-94f5-0732cde4feca.png)

### Data

initially, 400 observations

one was missing sqft, so dropped

next, looking at descriptive stats noticed one price listed as $350 - thought this seemed really unlikely - did some googling, address, 132 Commonwealth Ave, brownstone a few bloacks away from the charles river probably meant $350,000, but didn't want to assume decided to drop

also worried about max obs listed at $45,000,000 - but did some investigation, found the address listing online - found that 1 Franklin St is the millenium tower, according to LuxuryBoston.com, the entire 60th floor (aka "The Grand Penthouse") currently for sale - 360 degree balcony w/ views of Boston harbor and Charles river, 8 bedrooms, 12 bathrooms, 7 fireplaces, library, movie and game area, and staff quarters - despite absurdity of thise listing, I determined it was legit and kept it in the data - photos below for fun



![image](https://user-images.githubusercontent.com/78870884/113351414-dbb49b00-9308-11eb-9d0a-2cd84d6f62ff.png)


![image](https://user-images.githubusercontent.com/78870884/113351600-19b1bf00-9309-11eb-8b44-f7449050156b.png)


![image](https://user-images.githubusercontent.com/78870884/113351350-bf186300-9308-11eb-9a5f-5044a286618a.png)

After dropping the $350 house, I was left with 398 obervations - descriptive stats below


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


### Model Discription



### Output Analysis

MSE w/ just bed, bath, and sqft:  13635133589357.477

MSE w/ zips: 8768492452983.424

### Best/Worst Deals


Orig graphs
![image](https://user-images.githubusercontent.com/78870884/113357911-ca708c00-9312-11eb-9264-caad4953ea4c.png)

![image](https://user-images.githubusercontent.com/78870884/113357972-eecc6880-9312-11eb-8425-ddef2d63b419.png)

Zip graphs

![image](https://user-images.githubusercontent.com/78870884/113360607-1a9e1d00-9318-11eb-9dab-44a5a78ff974.png)

![image](https://user-images.githubusercontent.com/78870884/113360640-2c7fc000-9318-11eb-8cc9-e42072bc9eb1.png)



