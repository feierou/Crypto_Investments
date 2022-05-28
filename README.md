# Crypto_Investments


I am an advisor in one of the top five financial advisory firms in the world. Competitors are fierce, so I want to propose a novel approach to assembling investment portfolios that are based on cryptocurrencies. Instead of basing my proposal on only returns and volatility, I want to include other factors that might impact the crypto market—leading to better performance for your portfolio.


---

## Technologies

This project leverages Pandas, hvplot, KMeans, PCA, StandardScaler on Jupyter notebook

---

## Open Guide

Before running the application first open Jupyter lab in terminal:

```
  1. Activate dev environment by: "conda activate dev"
  2. Open Jupyter Notebook by: "Jupyter lab"
```


---

## Usage

To use the analysis simply clone the repository and run the **crypto_investments.ipynb** within the Jupyter Notebook.\
*Import the following libraries and dependencies:*

``` python
import pandas as pd
import hvplot.pandas
from path import Path
from sklearn.cluster import KMeans
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
```


---

## Import the Data

1. Use `pd.read_csv` to load the **crypto_market_data** into Pandas DataFrame.
2. Display the sample data and generate summary by `.head()` and `.describe()`.
3. Plot the data into line graph.

![<boken>](<Image/bokeh_plot.png>)

---

## Prepare the Data

1. Use `StandardScaler()` from scikit-learn to normalize the data from teh CSV file.
2. Create a DataFrame with scaled data. 
3. Copy the crypto names **coin_id** from the original data which is the **market_data**.
4. Set the **coin_id** as the index.

---

## Find the Best Value for K Using the Original Data

1. Create a list with the range from 1 to 11 for the number of k-values to try.
2. Create an empty list to store the inertia values.
3. Create a for loop to compute the inertia with each possible value of k. 
4. Create a dictionary with the data to plot the Elbow curve.
5. Create a DataFrame with the data to plot the Elbow curve.
6. Plot a line graph to display the Elbow curve with optimal value of K. 

![<original k>](<Image/original k.png>)

*From the graph, the best value for k is 4.*
---

## Cluster Cryptocurrencies with K-means Using the Original Data

1. Initialize the K-Means model using the best value for k which is 4. 
2. Fit the K-Means model using the scaled data.
3. Predict the clusters to group the cryptocurrencies using the scaled data.
4. Create a copy of the DataFrame.
5. Add a new column name **Crypto Clusters** to the DataFrame with the predicted clusters.
6. Create a scatter plot using hvPlot.

![<cluster k4>](<Image/cluster k4.png>)

---

## Optimize Clusters with Principal Component Analysis

1. Create a PCA model instance and set `n_components=3`.
2. Use the PCA model with `fit_transform` to reduce to three principal components.
3. Retrieve the `explained variance` to determine how much information 
can be attributed to each principal component.

*The total explained variance of the three principal components is 90%.*

4. Create a new DataFrame with the PCA data, set **columns** to `PC1, PC2, PC3`.
5. Copy the `coin_id` from the original data.
6. Set the `coin_id` column as index.

---

## Find the Best Value for k Using the PCA Data

1. Create a list with the range from 1 to 11 for the number of k-values to try.
2. Create an empty list to store the inertia values.
3. Create a for loop to compute the inertia with each possible value of k. 
4. Create a dictionary with the data to plot the Elbow curve.
5. Create a DataFrame with the data to plot the Elbow curve.
6. Plot a line graph to display the Elbow curve with optimal value of K. 

![<PCA elbow>](<Image/pca elbow.png>)

*The best value for k when using PCA is 4. There's no differ from the best k value found using original data.*

---

## Cluster Cryptocurrencies with K-means Using the PCA Data

1. Initialize the K-Means model using the best value for k which is 4. 
2. Fit the K-Means model using the scaled data.
3. Predict the clusters to group the cryptocurrencies using the scaled data.
4. Create a copy of the DataFrame.
5. Add a new column name **Predicted Cluster** to the DataFrame with the predicted clusters.
6. Create a scatter plot using hvPlot.

![<PCA cluster>](<Image/cluster pca.png>)

---

## Visualize and Compare the Results

**Elbow Curve**
![<original k>](<Image/original k.png>)
![<PCA elbow>](<Image/pca elbow.png>)

**Cluster Scatter**
![<cluster k4>](<Image/cluster k4.png>)
![<PCA cluster>](<Image/cluster pca.png>)

*The impact of using fewer features to cluster the data using K-Means makes the spread more concentrate which makes the visualization easier to tell the cluster groups.*

---
## Contributer

Feier Ou 

ffeierou1003@gmail.com 

---

## License

Feier Ou 
