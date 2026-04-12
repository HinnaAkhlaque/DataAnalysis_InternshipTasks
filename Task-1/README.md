**Task 1: Exploring and Visualizing the Iris Dataset**

**Objective:**

The objective of this task is to understand how to load, explore, summarize, and visualize a dataset using Python libraries such as pandas, matplotlib, and seaborn.

**Approach:**

Loaded the dataset using pandas from a CSV file
Explored dataset structure using:
  .shape
  .columns
  .head() & tail()
  .info() and .describe()
Checked for missing values and data distribution
Created visualizations using matplotlib and seaborn:
Scatter plot (relationship between variables)
Histogram (data distribution)
Box plot (spread and outliers)

**Results and Insights:**

Iris-setosa is clearly separable from other species based on feature distribution.
Petal length shows a strong distinction between species and is the most useful feature for classification.
Sepal length and width show overlap, making them less effective for classification.
Iris-versicolor and Iris-virginica show some overlap, requiring multiple features for accurate classification.
