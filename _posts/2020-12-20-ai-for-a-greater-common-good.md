---
layout: post
title:  "Dimensionality reduction using random projects"
date:   2020-12-20 10:45:11 +0200
categories: jekyll update
---

Let’s get a bit technical for one time. In this short blog post, we are going to look at dimensionality reduction. To reduce the dimensionality of your data, you can use various kinds of techniques. Some of the most common ones are:

- Missing value ratio
- Low variance filter
- High correlation filter
- [Random forest](https://de.wikipedia.org/wiki/Random_Forest)
- [Backward feature elimination](https://en.wikipedia.org/wiki/Feature_selection)
- [Forward feature selection](https://en.wikipedia.org/wiki/Feature_selection)
- [Factor analysis](https://en.wikipedia.org/wiki/Factor_analysis)
- [Principal component analysis (PCA)](https://en.wikipedia.org/wiki/Principal_component_analysis)
- [Independent component analysis](https://en.wikipedia.org/wiki/Independent_component_analysis)
- Methods based on projections
- [t-distributed stochastic neighbor embedding (t-SNE)](https://en.wikipedia.org/wiki/T-distributed_stochastic_neighbor_embedding)
- [Uniform manifold approximation and projection](https://en.wikipedia.org/wiki/Nonlinear_dimensionality_reduction)

For now, we only consider a projection method. Random projections to be more precise. But why is dimensionality reduction something we should care about? Let’s look at the problem from a high level first.

![IDC Global datasphere growth by region](https://thumbor.forbes.com/thumbor/960x0/https%3A%2F%2Fblogs-images.forbes.com%2Ftomcoughlin%2Ffiles%2F2018%2F11%2FGlobal-Datasphere-by-Regions.jpg)

We are generating an enormous amount of data every day. Even more importantly, just in the past five to ten years, we have generated an order of magnitude more than data than there was ever before in human history. The numbers are nuts! So, as data generation and data collection keep increasing in volume, visualizing the data and making sense of it becomes an ever-greater challenge, especially when we get more and more nuanced data with high dimensional representations. One solution to go about this problem is, oh "quelle surprise", dimensionality reduction. The basic concept is that you can reduce the complexity of data by dropping features represented in a vector space and, at the same time, maintain a high degree of explainability for the variation in the data. In order words, you want to take away aspects of data while minimizing the information loss. As a result, you can visualize high-dimensional data and make inferences.

But there are more benefits to dimensionality reduction. Some of them include:

Reduction in time and space complexity
Make otherwise not well-suited algorithms more applicable again
Potentially improves the performance of your analytics models

There are two distinct approaches to reduce dimensionality. You can either keep the most relevant variables (feature selection) or find a smaller set of new variables based on a combination of the original information (dimensionality reduction).

Random projections
But now, let’s get serious here. If we make random projections, we project an NxD matrix “A” to “A‘” (that is a matrix NxP, P < D) by means of Aq = A’ where q is a DxP matrix with almost random values. Just almost random values since each column must have a unit length. Meaning, every vector must sum up to 1.

To be clear, this approach generally leads to less accurate results than the ones from, for example, PCA or [singular value decomposition](https://en.wikipedia.org/wiki/Singular_value_decomposition). However, there are two major benefits to this methodology:

You can perform this operation without having to keep q in memory (cause you can generate its vectors multiple times using a seeded random number generator)
Increase processing time significantly (O(d<sup>2</sup> x n + d<sup>3</sup>) versus O(ndx) where d is the size of the projection subspace)

Enough of theoretical stuff. Let’s look at how it practically performs compared to PCA. Consider a dataset containing 2D data with two clusters around the points (2,2) and (8,8).

The graphic below shows five random projects to 1D for both the random projects and the PCA. We know from the previous graphic that there was a clear separation between the two clusters in 2D. Now, the random projection method was able to partition three of the five projections even though we’re using only half the space (we reduced the dimensionality from 2D to 1D). The second even looks pretty similar to the result from the PCA at the very bottom.

So, how about some higher dimensions? To figure out, we generate the same cluster as before but with some additional dimensions. We take the arbitrary number 10. Thus, we generate the data points around (2,2,2,2,2,2,2,2,2,2) and (8,8,8,8,8,8,8,8,8,8). To visualize this dataset, we encounter some challenges. We can either choose a scatterplot that does not add any meaningful value, I’d argue, or we can make a 2D tour through the 10D space.

Now that we have a 10D dataset, let’s also see how random projections perform compared to PCA when projecting the points to a 1D space. As we can see, the random projection is doing pretty poorly. Only one of the five projections is somewhat able to separate the two original clusters. How does this look like when we only reduce to 2D?

Without a doubt, PCA still gets the job done the cleanest. As we can see, the PCA represents the data on the x-axis as the two different clusters and on the y-axis as the cluster variance. That’s why it’s also easy to project the data to 1D. We only need the first principal component. As for the random projections, we see that they went quite well. Only one of the runs lead to a somewhat intertwined representation of the clusters where we can’t separate the two linearly.

To sum up, I’d argue that this approach is rather interesting to explore when you have high dimensional data that you need to get processed super-fast. In this quick and dirty experiment, I used a contrived dataset and a pretty aggressive approach to reduce its dimensionality to 1D. I wonder what, if any at all, difference there would be with sparse data.
