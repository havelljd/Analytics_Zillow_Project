# Analytics_Zillow_Project
This was a fun project that helped to understand and predict some of the Utah housing data provided by Zillow during peak pandemic real estate frenzy (2021). This was a group project that hooked into an API that scraped Zillow housing data, ran transformations and cleaned the data, and drew analysis from that data. At the time, real estate was booming, so we decided to see what predictions we could make regarding pricing and real-time data if we were to list a house. Our models aimed to take in some general housing information and return whether or not the property would be a good buy for the area. 

After getting the data we wanted from an API, we did a little bit of cleaning and this was our dataframe we worked with in pandas:

<img width="1092" alt="image" src="https://user-images.githubusercontent.com/8563653/211221463-b678f204-2efc-4c5a-94e6-9c69ebdadeb8.png">

With this data, we started out with some regression modeling to predict price of a home listed in Utah. We dummy coded categorical variables (converting  non-numerical data into numbers) and displayed the VIF score for each feature to analyze multicollinearity. The higher the VIF score, the more likely it is to be correlated with other features.

<img width="266" alt="image" src="https://user-images.githubusercontent.com/8563653/211221797-6fa5096f-0675-4da7-89f7-3046c576362a.png">

We then determined which regression model would be most accurate when predicting price. The result was a regression XGBoost would be best.

<img width="186" alt="image" src="https://user-images.githubusercontent.com/8563653/211221855-70737a85-feff-4aa1-b839-de289d52292f.png">

After creating the model, we ran some predictions to predict price of a given home, which should help decide if (for monetary value / investing reasons) a house you want to buy is undervalued.

<img width="184" alt="image" src="https://user-images.githubusercontent.com/8563653/211221998-79c1d3c3-29ea-4b8b-8e6b-e617c7966aec.png">

After regression modeling, we ran some classification modeling to try and guess zip code of a listing. This was more of a requirement, honestly, for the class. 

<img width="311" alt="image" src="https://user-images.githubusercontent.com/8563653/211222057-be6ec89b-2e72-43f8-81f6-549202cbd220.png">

Then we did some classification modeling! First we checked a few things to get the optimal number of clusters. First analyzed the Calinski-Harabasz criterion to check how many clusters our model should have:

<img width="310" alt="image" src="https://user-images.githubusercontent.com/8563653/211222437-c3e28b53-b575-43a5-b7e3-631f152084e4.png">

Then the silhouette analysis to check similarity of a point in it's cluster to other clusters:

<img width="298" alt="image" src="https://user-images.githubusercontent.com/8563653/211222516-33dd91ed-a17c-43ac-bc1d-17c061d69bff.png">

And finally the elbow method: 

<img width="368" alt="image" src="https://user-images.githubusercontent.com/8563653/211222538-85a8f27e-6b35-4c38-a126-c95777afd032.png">

We ended up with 5 separate clusters for our model. After assigning each row its cluster, we then trained a model to predict price. Super fun project that really taught me that there's a lot of factors that go into buying a house; what would be interesting is looking at future economic numbers and seeing if WFH or income or what really caused the housing feeding frenzy from 2020-2021.
