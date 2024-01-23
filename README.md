# Grouping Customer Characteristics by Bandwidth Usage With K-Means Clustering

## About
In general, higher bandwidth subscriptions cost more and therefore bring more revenue for an ISP. The Customer Churn data set contains a field named Bandwidth_GB_Year, which is measured in GB used per year. Histograms can be used to identify high or low range users by other categorical fields like Area or PaymentMethod. Furthermore, classification algorithms can be applied to predict which bandwidth use ranges correlate with such categories. Such classifications may not be so apparent when compared to other continuous attributes. Perhaps there is a distinct difference in bandwidth use for customers by Tenure, Income, or other continuous fields included in this data set. Being able to make distinctions like this may then be worthwhile for marketing purposes.

A customer's income, for instance, could be arbitrarily subsetted into discrete intervals so that bandwidth usage could be fitted to a classification model to make predictions. This kind of approach may risk neglecting to detect a clustering of bandwidth usages that correspond with a less arbitrary range of incomes. Attempts to apply classification models when comparing the relationships between continous variables seems to fail in this regard. Regression can provide a means of predicting individual outcomes, but give no indication on how to group either predictor or target variables. An unsupervised machine learning algorithm that groups data points according to distance measures may be better at classifying relational correspondences through clustering. Such techniques provide means of discovering patterns and natural clusters amongst data. (DataCamp)

Given that high bandwidth users generate more revenue for an ISP it would then seem worthwhile to get the most out of existing data to identify segments of customers by continuously defined characteristics. To that end is it possible to identify a distinguishable range of incomes that correspond with high bandwidth users? What about other continuous factors such as the population of customer locale, outage time experienced, bill amount, age, or other possible features? Is there a measurable way to determine which relationship produces the most distinguishable segmentation in order to prioritize marketing efforts?

## Clustering Techniques and Assumtions
One way of clustering data begins with a single point then finds the closest neighbor via Euclidean distance. A centroid of these 2 points can be computed as the mean distance between the 2 points, and used as a reference to find the nearest distance of a 3rd data point. The inclusion of more and more points in this manner form a cluster. Centriods of clusters can then be used as endpoints from which distances to other clusters are computed. Such a bottom up algorithm describes hierarchical clustering. A set of random points would need to be specified to start with before carrying out the rest of the subsequent calculations, and the results of clustering after a certain number of iterations may differ depending on which original random points where initially selected. This may lead to a computationally expensive process.

Another way of forming clusters begins with computing the centroid of a randomly selected number of points. Distances between such collections are computed between respective centroids. A certain number of clusters can be specified, so that the distance between respecitve clusters is maximized. This gives a more computationally efficient means of clustering data points since more points are considered at each iteration than with the hierarchical method. This way of categorization is called K-Means Clustering, and is particularly appropriate for large data sets, especially if there is a need to cluster amongst multiple features.

Hierarchical clustering can produce a visual representation of the formations via a dendrogram which represents groupings in a sort-of upside down binary tree diagram where higher level cluster distances are indicated along the y-axis. (Pai, 2021.). When applying K-Means clustering in Python a pair of cluster centers and distances between clusters is implicit to the syntax of returnable objects. This makes it possible to create an "elbow plot" of cluster distances against number of clusters. As the number of clusters increases there should be a relatively discernable point on this plot where the rate of decrease in distance becomes more apparent. In terms of calculus, a second derivative would have a higher magnitude and imply a greater degree of concavity at such a point. In other words, looking at such a plot gives an erzats quantifiable indication of optimal number of clusters. The severity of the bend in this kind of plot provides insight into how distinct the clusters are.

There are several continuous candidate target variables for which to attempt clustering bandwidth usage by in this data set. Unfortunately, looking at binary plots of each it becomes rather noticeable that there are generally 2 clusters for each. The goal of this project is then to use K-Means clustering and elbow plots to determine which continuous relationship with bandwidth usage results in the most pronounced clustering.

## Packages Used
The data was processed, modelled and analyzed using Python. The following packages and libraries were used:

Pandas: general dataframe handling

warnings: ignore uneccesary warnings that don't affect outcomes of data operations

sklearn

preprocessing
StandardScaler - normalizing/standardizing
scipy - usupervized machine learning package

cluster - clustering
kmeans - compute centroids and distances (distortions)
vq - labelling clusters
matplotlib.pyplot: plotting and graphics

seaborn extension of matplotlib, emphasis on ease of using dataframes
