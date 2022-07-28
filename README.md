# Cryptocurrencies

## Overview of the analysis

Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. I created a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.
However, the data provided was not ideal, so it needed to be processed to fit the machine learning models. Since there was no known output for what we were looking for, I used unsupervised learning. To group the cryptocurrencies, I implemented a clustering algorithm and used data visualizations to share the findings with the board.

## Results

### Preprocessing the Data for PCA

Using Pandas, I preprocessed the dataset in order to perform PCA on the data. I kept all the cyrptocurrencies that are being traded, dropped the IsTrading column, removed the rows that had at least one null value, filtered the DataFrame so only rows where mined coins remained, created a new DataFrame that holds only the cryptocurrency names, and removed the CoinName column. 

### Reducing Data Dimensions Using PCA

Utilizing the preprocessed data, I applied PCA to reduce the dimensions to three principal components. A new DataFrame was created that includes a PC 1 column, PC 2 column, and PC 2 column.

![PC Columns](https://github.com/jstearns1988/Cryptocurrencies/blob/main/Resources/PC%20Columns.png?raw=true)

### Clustering Cryptocurrencies Using K-means

An elbow curve using hvPlot was created to find the best value for K.

![Elbow Curve](https://github.com/jstearns1988/Cryptocurrencies/blob/main/Resources/elbow%20curve.png?raw=true)

The K-Means algorithm was run to make predictions of the K clusters for the cryptocurrencies' data. A new DataFrame was created by concatenating the previously created DataFrames on the same columns. Next, the CoinName column that holds the names of the cryptocurrencies created earlier was added. Another new column named Class that holds the predictions was created and resulted in the following clustered DataFrame.

![Clustered DF](https://github.com/jstearns1988/Cryptocurrencies/blob/main/Resources/Clustered%20DataFrame.png?raw=true)

### Visualizing Cryptocurrencies Results

The predicted K clusters for the cyptocurrencies' data was then used to create a 3D scatter plot using the Plotly Express scatter_3d() function to plot the three clusters.

![3d Scatter Plots](https://github.com/jstearns1988/Cryptocurrencies/blob/main/Resources/3d%20Scatter%20Plots.png?raw=true)

The CoinName and Algorithm columns were added to the hover_name and hover_data parameters so each data point would show them on hover. Then a table with tradable cryptocurrencies was created using the hvplot.table() function.

![Tradable Currencies](https://github.com/jstearns1988/Cryptocurrencies/blob/main/Resources/Tradable%20Currencies.png?raw=true)

Using the MinMacScaler().fit_transform method, I scaled the TotalCoinSupply and TotalCoinsMines columns between the given range of zero and one. A new DataFrame that scaled the data previously created was implemented. The Class column was added to the new DataFrame.

![Total Coins Supply](https://github.com/jstearns1988/Cryptocurrencies/blob/main/Resources/Total%20Coins%20Supply.png?raw=true)

To complete this analysis, I created an hcplot scatter plot to visualize the data.

![Scatter Plot](https://github.com/jstearns1988/Cryptocurrencies/blob/main/Resources/Scatter%20Plot.png?raw=true)

## Summary

Performing this Unsupervised Machine Learning analysis identified 532 tradable currencies currently on the market.
