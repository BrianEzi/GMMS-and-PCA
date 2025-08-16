# GMMS-and-PCA

# Analysis of FMNIST Dataset using PCA and GMMs

This project analyzes the Fashion MNIST (FMNIST) dataset, a collection of 70,000 grayscale images of fashion products. The analysis uses Principal Component Analysis (PCA) for dimensionality reduction and Gaussian Mixture Models (GMMs) for unsupervised clustering.

## Dataset

The FMNIST dataset consists of 70,000 grayscale images, each 28x28 pixels, representing 10 distinct fashion product classes. The dataset is split into a training set of 60,000 images and a test set of 10,000 images. A subset of 10,000 images was used for this analysis.

## Methods

### 1. Principal Component Analysis (PCA)

PCA was used to reduce the dimensionality of the FMNIST data from 784 pixels per image to a smaller, more manageable set of principal components (PCs). The key steps included:

* **Normalisation:** Pixel values, originally in the range of [0, 255], were scaled to [0, 1] to ensure all features had comparable magnitudes.
* **Dimensionality Reduction:** The analysis focused on the first 10 principal components, which together captured approximately 72% of the total variance in the data.
* **Visualisation:** Scatter plots of the first two principal components were created to visualise the data in a reduced space, revealing some class separation but also significant overlap between similar items like T-shirts and Shirts.
* **Interpretability:** Correlation loadings plots and heatmaps were generated to show how original pixel values contributed to the principal components, confirming that the PCs captured meaningful features such as edges and contours.

### 2. Gaussian Mixture Models (GMMs)

Following dimensionality reduction, GMMs were applied to the data's top 10 principal components to perform unsupervised clustering.

* **Model Fitting:** GMMs were fitted with a range of components (2 to 15) to find the optimal number of clusters.
* **Model Selection:** The optimal number of clusters, as determined by the Bayesian Information Criterion (BIC), was 15. However, the BIC was found to be ineffective for this task as it favored more complex models, and the correct number of classes (10) was difficult to identify.
* **Performance:** The GMM clustering resulted in a high misclassification rate of 52.26% with 15 clusters. When the number of clusters was manually set to the true number of classes (10), the misclassification rate improved to 38.84%.

## Conclusion

The project successfully used PCA to reduce the FMNIST dataset's dimensionality and GMMs to explore its intrinsic structure. PCA was effective in retaining most of the data's variance, but its linear nature meant it struggled with overlapping class features. The GMM analysis showed that while the model could find some structure, its performance was limited by the high degree of overlap between classes and the loss of critical information during PCA.

## Future Work

Future improvements could include:

* Using non-linear dimensionality reduction techniques like t-SNE or UMAP to better preserve complex data structures.
* Exploring alternative clustering methods such as hierarchical clustering or DBSCAN.
* Using deep learning for feature extraction and clustering.
* Evaluating cluster quality with external metrics like the Adjusted Rand Index in addition to BIC.
