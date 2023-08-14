### **optimal_clusters**

we work with two well known methods of finding optimal clusters for kmeans clustering: (1) Elbow method - iterates through a number of clusters and then we choose the number where there's a sharp dip in the error. (2) Silhouette method - it is a measure of how similar a data point is within a cluster compared to other clusters. We choose the cluster that maximizes the silhouette score.

### **EllipticEnvelope**

after scaling the data, we use sklearn's method/object 'EllipticEnvelope' which detects outliers in a gaussian distributed dataset. We can choose the contamination parameter to our liking. 
