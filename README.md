# ElbowPlot

ElbowPlot is a Python library designed to facilitate the visualization of the optimal number of clusters in K-means clustering through the elbow method. This method is particularly useful in unsupervised learning to determine the ideal number of clusters by identifying the point at which the within-cluster sum of squares (WCSS) begins to diminish, forming an "elbow".

## What is the Elbow Method?

The elbow method plots the values of the WCSS as the number of clusters increases. WCSS is the sum of squared distances between each point and the centroid in a cluster. As the number of clusters increases, WCSS continues to decrease as points will be closer to the centroids they are assigned to. The goal is to identify the number of clusters where the decrease in WCSS begins to level off (forming an elbow). Choosing the number of clusters beyond the elbow will not result in significant gains in performance and may lead to overfitting.

## Installation

You can install ElbowPlot directly from PyPI:

```bash
pip install elbowplot
```

## Dependencies

ElbowPlot requires the following Python libraries:
- NumPy
- Matplotlib
- scikit-learn

These dependencies will be automatically installed when you install ElbowPlot.

## Usage

### Basic Example

Here's a simple example demonstrating how to use ElbowPlot with a synthetic dataset:

```python
import numpy as np
from elbowplot.core import elbow_plot

# Generate some random data
np.random.seed(0)
data = np.random.rand(150, 2)  # 150 points in 2 dimensions

# Determine the optimal number of clusters by visualizing the elbow plot
elbow_plot(data, 10)  # Test from 1 to 9 clusters
```

### Output

When you run the above code, you will see a plot with the number of clusters on the X-axis and the inertia (WCSS) on the Y-axis. The plot will have points marked for each number of clusters tested, and a line connecting these points. Look for the point where the inertia begins to decrease at a slower rate, which typically resembles an "elbow".

### Understanding the Output

When you run the `elbow_plot` function, it generates a line plot that visualizes the relationship between the number of clusters and the within-cluster sum of squares (WCSS), also known as inertia. Here's what you should look for in the plot:

- **X-axis**: Represents the number of clusters tested. In the example provided, this ranges from 1 to 9 clusters.
- **Y-axis**: Represents the inertia for each cluster count. Inertia is calculated as the sum of the squared distances between each point and its nearest cluster center.

#### Key Features of the Plot

- **Data Points**: Each point on the plot corresponds to the inertia calculated with a specific number of clusters.
- **Line Connecting Points**: A line connects these points, making it easier to see the rate at which inertia decreases as the number of clusters increases.

#### Identifying the Elbow

The "elbow" point on the plot is the key feature to look for. It represents the number of clusters at which the decrease in inertia shifts from being rapid to more gradual. Here’s how you can identify it:

1. **Rapid Decline**: Initially, as you increase the number of clusters from 1 onwards, the inertia decreases sharply.
2. **Leveling Off**: After a certain number of clusters, this decrease slows significantly, indicating that adding more clusters does not contribute significantly to gaining better clustering performance. This point of inflection is known as the "elbow".

#### Example Interpretation

If the elbow occurs at 4 clusters, this suggests that increasing the number of clusters beyond 4 will result in diminishing returns in terms of lowering inertia. Thus, 4 can be considered an optimal number of clusters for the given data.

### Visual Example

Below is a theoretical representation of an elbow plot:

![elbow-method](Image/elbowmethod.png)

## Contributing

Contributions to ElbowPlot are welcome! Please fork the project, make your changes, and submit a pull request on GitHub.

## License

ElbowPlot is open-source software licensed under the MIT license. See the LICENSE file for more details.
