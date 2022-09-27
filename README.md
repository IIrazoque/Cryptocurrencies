# Cryptocurrencies

Accountability Accounting is interested in offering a new cryptocurrency investment portfolio for its customers. Our goal is to create a report on what cryptocurrencies are on the trading market and how they could be grouped as a classification system for this new investment.
We first started loading in our crypto data and removed non-relevant columns (figure 1). We process the Data by re-formatting non-numeric columns. Once we obtained a clean dataset (figure 2) we are to apply unsupervised machine learning models to help determine any meaningful patterns. 

*Figure 1. Loading and cleaning csv file*

![This is an image](https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image1.PNG)
 
Loaded the crypto_data csv and kept data with active trading. The figure below shows a reduction in data points from 1252 to 1144. 
Next, we continue to clean our dataset by removing null values and any columns that provided meaningful information such as TotalCoinsMined. 

*Figure 2. Removing rows of empty data*

![This is an image](https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image2.PNG)
 
To create clusters for unsupervised learning we use the k-mean algorithm. Which is finding the “means” of all data points in a cluster. Then train this model to fit the data to the nearest centroid for each cluster. The predict() method will assist in generating the number of predicted labels.
We can use the Trail & Error methods to blindly guess the number of clusters, but to ease this guessing-game we can created an elbow curve to help measure the amount of variation in the dataset. The issue we run into is overfitting data. The Principal Component Analysis (PCA) can help by reducing the dimensions. 

*Figure 5. Crypto Dataframe*

![This is an image](https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image5.PNG)
 

## Deliverable 1: Preprocessing the Data for PCA

Before we scale our dataset, we need to convert the “Algorithm” and “ProofType” columns into readable categories for algorithms to process, which is encoding these into 0’s and 1’s. We used the get.dummies function to get these columns in numerical category for scaling (Figure 6).

*Figure 6. Creating dummies Variables For Categorical Data*

![This is an image]( https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image6.PNG)
 
We then use the StandardScaler().fit_transform function to scale the dataset.

## Deliverable 2: Reducing Data Dimensions Using PCA

To initialize PCA analysis we first created categorical indicators for Algorithm and ProofType columns. Our StandardScaler method generated ~98 indicators, which can be is a large number to work with... We reduced this dimension to 3 components (PCA): principal component 1, principal component 2,  and principal component 3. 

*Figure 3. PCA Data frame*

![This is an image](https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image3.PNG)
 

## Deliverable 3: Clustering Cryptocurrencies Using K-means

Once we created a Dataframe with the PCA’s we plug into an elbow curve (figure 4). The Elbow curve helps us determine the number of possible clusters. We then initialize the K-means model and fit the model to predict clusters. 

*Figure 4. Elbow Curve*

![This is an image](https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image4.PNG)
 
We then combine the data generated to create a final dataframe with crypto_clusters details, PCA, and CoinNames.

*Figure 7. Crypto_clusters Dataframe*

![This is an image](https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image7.PNG)

 


## Deliverable 4: Visualizing Cryptocurrencies Results

Created visual of these clusters in 3D and 2D scatter plots (Figure 8 & 9).

*Figure 8. 3D Scatter plot of PCA Data & Crypto Clusters*

![This is an image](https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image8.PNG)
 

*Figure 9. 2D Scatter Plot of Clusters in TotalCoinsMined vs TotalCoinSupply*
![This is an image](https://github.com/IIrazoque/Cryptocurrencies/blob/131fc00abcc56d2467ef35553529dd6e0aac5643/Images/Image9.PNG)

Both plots show us the same cluster behavior, 4 clusters but the class 2 is further away from the rest. Could be an outlier. 
