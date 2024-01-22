# UMAP
UMAP is a dimensionality reduction technique that can be used for visualizing high-dimensional dataset structure through embedding in two or three dimensions.

The algorithm converts high-dimensional Euclidean distance between datapoints into an approximate probability representing similarity under a Gaussian distribution centered on each point.

Given input data X with N samples and M features, the local distance distributions are modeled as:

$$p_{j|i} = \frac{exp(-||x_i - x_j||^2)}{\sum_{k \neq i} exp(-||x_i - x_k||^2)}$$

Where x represents the feature vectors. This models fuzzy topological representation of nearby points.

UMAP then searches the low dimensional space Y to optimize the positions of the embedded points. Similarities between points in the embedding space are defined using cross entropy between the local fuzzy simplicial sets S of the original space and the low dimensional representation R as:

$$H(S,R) = \sum_{i=1}^{N} p_{i} \sum_{j \in N_i} p_{j|i} \log \frac{p_{j|i}}{q_{j|i}}$$

Where:

$$q_{j|i} = \frac{a_{i,j}}{\sum_{k \in N_i} a_{i,k}} \
a_{i,j} = \frac{1}{\alpha(1 + d(y_i, y_j)^2)^\beta}$$

Here a_{i, j} represent the similarities in the low dimensional space, defined using a Student t distribution. The locations of the embedded points in Y are updated using stochastic gradient descent to optimize this cross entropy loss.

The advantages of UMAP over t-SNE and other techniques include superior runtime performance for large data sizes, better preservation of global data structure alongside local neighborhoods, and direct support for out-of-sample extensions for embedding new unseen data.

The ability of UMAP to meaningfully embed dataset structure in lower dimensions provides an effective exploratory analysis and visualization technique for machine learning applications such as identifying clusters and outliers. The 2D projections allow quicker insights into patterns compared to inspection of higher dimensional raw data.

The UMAP algorithm has additional capabilities including support for discrete categorical input data, different distance metrics, uniform manifold signals on unknown manifold shapes, etc. The embeddings generated provide a useful unsupervised analysis foundations for tasks like clustering, classification and retrieval.
