# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Start the program.
2.Import required libraries like pandas, matplotlib, and sklearn.
3.Load the Mall_Customers.csv dataset.
4.Select Annual Income and Spending Score as features.
5.Initialize an empty list to store WCSS values.
6.Apply K-Means for cluster values from 1 to 10.
7.Store inertia (WCSS) for each cluster value.
8.Plot the Elbow graph to find the optimal number of clusters.
9.Train K-Means again using the chosen number of clusters (e.g., 5).
10.Predict clusters, assign them to customers, and visualize the clusters using scatter plot.

## Program:
```

Program to implement the K Means Clustering for Customer Segmentation.
Developed by: DEEKSHA VICTOR SELVAKUMAR SINDHUPRIYA
RegisterNumber: 212225230041

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++",n_init=10)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters=5, n_init=10)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster2")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster4")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="pink",label="cluster5")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img width="888" height="548" alt="image" src="https://github.com/user-attachments/assets/a1435b3d-6631-43c1-8e06-e06c66501bc0" />
<img width="777" height="238" alt="image" src="https://github.com/user-attachments/assets/bbc8e991-603a-490b-b8e5-b8f46025ee83" />
<img width="890" height="520" alt="image" src="https://github.com/user-attachments/assets/d0fc4c79-af0b-468f-b10e-9a511aeeaf82" />
<img width="883" height="605" alt="image" src="https://github.com/user-attachments/assets/223a2fc1-40ff-4268-8f6b-f1371be4564d" />


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
