# cryptoclustering
## Prepare the Data
I began by reading in the data from the csv, and previewing the data.
After that, I ran it through the StandardScaler() module to normalize the data since there can be extremely large variance with crypto values and growth.ds
Then I created a DataFrame of the standardized data setting the index to each crypto coin. I ran into an issue here because I forgot to put Inplace=True, but I fixed that fairly quickly.

## Finding k and creating clusters with K
Once I did that I began the process of creating the elbow plot to determine the best value for K.
I initialized a list of kmeans from 1-11 and an empty list for the innertia.
I ran a for loop for i in k to create the values to fill in for inertia by fitting it to the standardized data frame.
After, I plotted a line with the values of k and inertia and found that 4 was likely the best choice since there was a significant drop off in inertia from 3 to 4, but a much smaller one from 4 to 5.

Once I decided on 4, I initialized KMeans with 4 being the number of clusters, fit it to the dataframe, and used the prediction function to create the clusters.
The clusters were then added to a copy of the dataframe and plotted in a scatter plot, which created decently tight clusters, but there was some overlap between clusters as well.

## Finding k and creating clusters with PCA
I used pca to simplify the data by removing excess variables, which was able to explain 88 percent of the variance between data according to the explained variance function.
I then repeated the process of creating the elbow plot with the new pca data to determine the best value for k to create clusters. Again that value was 4, and it was clearer this time than before.
I then used kmeans with a 4 clusters and the new pca dataframe to predict the clusters for the new data and created a scatter plot to show the data.
Using PCA achieved much clearer and tighter clusters than using KMeans did, which can be seen by analyzing the side by side elbow and scatter plots at the end of the code.
