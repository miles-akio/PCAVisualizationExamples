# PCA – Exploratory Data Analysis with Principal Component Analysis

---

In this project, I explore how **Principal Component Analysis (PCA)** can be applied to different types of datasets to uncover hidden patterns, reduce dimensionality, and visualize complex data.

The project demonstrates:

* Replicating Andrew Ng’s PCA example.
* Visualizing how PCA works on a small 2D dataset, showing that not every projection is equally effective.
* Understanding how 3D data can be represented in a 2D subspace.
* Applying PCA to a high-dimensional dataset to reveal clusters that are not obvious in the raw features.

---

## 📦 Libraries Used

```python
import pandas as pd
import numpy as np
from sklearn.decomposition import PCA
from pca_utils import plot_widget, random_point_circle, plot_3d_2d_graphs
from bokeh.io import show, output_notebook
from bokeh.plotting import figure
import matplotlib.pyplot as plt
import plotly.offline as py
import plotly.express as px
```

---

## 🔹 Part 1: Replicating Andrew Ng’s PCA Example

I started by working with the same toy dataset Andrew Ng showed in the lecture:

```python
X = np.array([[ 99,  -1],
              [ 98,  -1],
              [ 97,  -2],
              [101,   1],
              [102,   1],
              [103,   2]])
```

* Using PCA with 2 components, I found that the **first principal component retained 99.24%** of the information.
* When reducing to just 1 component, the dataset was still well represented (since that axis contained almost all the variance).
* Visualizing the inverse transform showed how the data compressed to a single line when using just one dimension.

This demonstrated that PCA can dramatically reduce dimensions without losing much information.

---

## 🔹 Part 2: Visualizing PCA in 2D

I generated 10 random points in a plane and explored how PCA projects them:

* Some projections compressed different points into the same location (bad projection).
* PCA automatically finds the line that maximizes separation between points.
* Using an interactive widget, I could rotate the projection line and visually see why PCA’s choice is optimal.

---

## 🔹 Part 3: 3D to 2D Visualization

I created 150 random points in 3D space on a circle and used PCA to reduce them into 2D.

* The result showed that PCA can **flatten 3D data into 2D while preserving structure**.
* This was visualized using both static and interactive 3D/2D scatterplots.

---

## 🔹 Part 4: High-Dimensional Dataset (500 samples × 1000 features)

To test PCA on real high-dimensional data, I loaded a **toy dataset** with 500 samples and 1000 features.

Steps:

1. I checked random feature pairs → scatterplots revealed no clear patterns.
2. I computed correlation across all features → the maximum correlation was only about 0.63, so not much structure appeared.
3. I applied PCA with 2 components → the data projected into 2D revealed **well-defined clusters**!

   * Even though PCA preserved only **14.6% variance**, the structure became visible.
4. Extending PCA to 3 components increased variance preservation to **19%**, showing around **10 clear clusters** in 3D.

---

## 📊 Key Takeaways

* PCA can reveal **hidden structures** in high-dimensional data that are invisible in raw pairwise plots.
* Even when retaining a small fraction of variance, PCA can make clustering patterns much clearer.
* It’s a powerful tool for **dimensionality reduction, visualization, and exploratory data analysis (EDA)**.

---

## 📝 Exercises (Solved)

Here are the solved exercises from the project:

### Exercise 1: PCA on Andrew Ng’s Example

* **Variance explained by PC1:** \~99.24%
* **Variance explained by PC2:** \~0.76%
* Using only PC1 is sufficient to represent the dataset.

### Exercise 2: 10-Point PCA Projection

* Rotating the projection line shows that **not all 1D compressions are equal**.
* PCA chooses the line that maximizes variance (best spread).

### Exercise 3: 3D to 2D PCA

* Random points on a circle in 3D, when reduced to 2D, still showed circular structure.
* PCA effectively preserved the geometry.

### Exercise 4: High-Dimensional Dataset (500 × 1000)

* Pairwise scatterplots: **no visible pattern**.
* Correlation: weak max correlation (\~0.63).
* PCA (2D): revealed **clusters** despite only preserving \~14.6% variance.
* PCA (3D): improved variance to \~19% and showed **\~10 clusters** clearly.

---

## 🎯 Final Thoughts

Through this project, I demonstrated how PCA helps reduce dimensionality while retaining the most important information. Even when variance retention seems small, PCA can still uncover meaningful structures that are otherwise hidden.

---
