## K-means Clustering
- Data set: {x_1,...,x_N}
- N observations
- D dimensions
- K clusters

Goals: *Partion data into K clusters*.

- Clusters = group of data points whose inter-point distances are small compared with the distances to points outside of the clusters
- Centeroids ($\mu_k$): Center of clusters
	- Algorithm iteratively updates the positions of the $\mu_k$ to optimize the clustering objective function. 
	- Typically defined in terms of the distances between the data points and the centroids.

Updated Goal: 
1. *Assign points to cluster and set of centroids vectors {$\mu_k$}*
2. *Such that the sum of the squares of the distances of each point to it closest centroid $\mu_k$ is min*


- Binary Indicator ($r_{n,k} ∈ {0,1}$): Shows if point is in cluster or not. 
	- Chooses 1 for whick ever value of $k$ gives min value of $\lvert\lvert \boldsymbol{X} - \boldsymbol{\mu_{j}}\rvert\rvert^2$ 
		- For whichever value of $k$ gives the minimum value of the squared distance between the data point and the centroid vector $\mu_j$
	- Chooses 0 otherwise

When finding the min values of centroids of $\mu_j$ (optimizing it):

 - We can fix $rnk$ and only update values of centroids.
 	- This the assignment of data points to clusters does not change. Instead, only the positions of the centroids are updated to better represent the data points assigned to each cluster.
 - Doing this, we can minmize the objective function ($J$) by taking it's derivated wrt to $\mu_k$ as it becomes dependent on just $\mu_k$
 - We can then solve for $\mu_k$ to update it's value: 

 	$\mu_k$ = sum of product of r and data point / sum of r
 	

## How does relate to EM?

1. We choose some inital values for the centroids
2. Then we minimze the objective function $J$ wrt to $r$ with a fixed $\mu_j$
3. Then we minimze the objective function $J$ wrt to  $\mu_j$ with a fixed $r$
4. We repeat 2 and 3 until we converge
 - Convergence means that the values of the centroids and binary indicator variables have stabilized and no longer change significantly between iterations. At this point, the algorithm has found a local minimum of the objective function and has obtained a good clustering of the data

E-Step (step 2): "Expectation" step because we are estimating which data point belongs to each cluster.

- Computing $r$ given data points and current estmate of centroids

M-Step (step 3): "Maximazation" step because we are trying to maximize the likelihood of the observed data ($x$) given it's current assignment from $r$. 

- Computing values for the $\mu_j$ that maximize the expected log-likelihood found in the E-step




