# Cryptocurrency Clusters Unsupervised Machine Learning
## Background

- Goal is to create a report that includes what cryptocurrencies are on the trading market and determine whether they can be grouped to create a classification system for this new investment.
-  Process raw data to fit the machine learning models using unsupervised learning. Use several clustering algorithms to explore whether the cryptocurrencies can be grouped together with other similar cryptocurrencies. 

## Instructions

### Data Preparation

- Read `crypto_data.csv` into Pandas. The dataset was obtained from [CryptoCompare](https://min-api.cryptocompare.com/data/all/coinlist).

- Discard all cryptocurrencies that are not being traded. In other words, filter for currencies that are currently being traded. Once you have done this, drop the `IsTrading` column from the dataframe.

- Remove all rows that have at least one null value.

- Filter for cryptocurrencies that have been mined. That is, the total coins mined should be greater than zero.

- Ensure data is numeric. Since the coin names do not contribute to the analysis of the data, delete the `CoinName` from the original dataframe.

- Convert the remaining features with text values, `Algorithm` and `ProofType`, into numerical data. Use Pandas to create dummy variables

   ***The number of columns in the dataframe increased significantly due to the conversion. However, the number of rows stayed the same.*** ![image-20210924222013272](C:\Users\franc\AppData\Roaming\Typora\typora-user-images\image-20210924222013272.png)

- Standardize dataset so that columns that contain larger values do not unduly influence the outcome.

### Dimensionality Reduction

- Perform dimensionality reduction with PCA. Preserve 90% of the explained variance in dimensionality reduction. 

  ​	***The number of columns was reduced. Although the dimensions decreased, the variance percentage remains quite high. ***

  ![image-20210924222700349](C:\Users\franc\AppData\Roaming\Typora\typora-user-images\image-20210924222700349.png)

  

- Further reduce the dataset dimensions with t-SNE and visually inspect the results. In order to accomplish this task, run t-SNE on the principal components: the output of the PCA transformation. Then create a scatter plot of the t-SNE output. Observe whether there are distinct clusters or not.

  ​	***The t-SNE reduced data to two columns. One cannot see any distinct clusters in the scatter plot shown below. ***

  ![image-20210924224143456](C:\Users\franc\AppData\Roaming\Typora\typora-user-images\image-20210924224143456.png)

### Cluster Analysis with k-Means

- Create an elbow plot to identify the best number of clusters. Use a for-loop to determine the inertia for each `k` between 1 through 10. Determine, if possible, where the elbow of the plot is, and at which value of `k` it appears.

  ![image-20210924230656702](C:\Users\franc\AppData\Roaming\Typora\typora-user-images\image-20210924230656702.png)

### Recommendation:

***Based on the K-means Elbow plot and the t-SNE scatter plot, I did not find any meaningful or distinct number of clusters to recommend. *** 
