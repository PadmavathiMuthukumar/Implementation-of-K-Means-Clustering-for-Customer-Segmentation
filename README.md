# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages using import statement.
2. Read the given csv file using read_csv() method and print the number of contents to be 
   displayed using df.head().
3. Import KMeans and use for loop to cluster the data.
4. Predict the cluster and plot data graphs.
5. Print the outputs and end the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Padmavathi M
RegisterNumber:  212223040141
*/
```
```

import pandas as pd
import matplotlib.pyplot as plt

data = pd.read_csv('Mall_Customers.csv')

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = [] #Within-Cluster Sum of Square.
#It is the sum of squared distance between each point & the centroid in a cluster

for i in range(1,11):
    kmeans = KMeans(n_clusters = i, init = "k-means++")
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11), wcss)
plt.xlabel("Number of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])
KMeans(n_clusters = 5)

y_pred = km.predict(data.iloc[:, 3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```
## Output:
## Dataset:
![Screenshot 2024-10-29 110710](https://github.com/user-attachments/assets/68a956a6-f5b7-4e8d-8bb1-081f1ace3119)
## Dataset Information:
![Screenshot 2024-10-29 110721](https://github.com/user-attachments/assets/1d5747aa-6acd-4187-8cbd-f0baec801a07)
![Screenshot 2024-10-29 110734](https://github.com/user-attachments/assets/9cbf5dd6-c7f7-4046-ab28-5bb64400c0a1)
## Elbow Method Graph(wcss vs each iteration):
![Screenshot 2024-10-29 110750](https://github.com/user-attachments/assets/b303962b-8755-400b-810d-ecc253d0583f)
![Screenshot 2024-10-29 110801](https://github.com/user-attachments/assets/c84547c1-d753-4285-a17e-5ac06fcea529)
## Clustering representing customer segments-graph:
![Screenshot 2024-10-29 110812](https://github.com/user-attachments/assets/ee8db9a0-e7ce-40c8-a420-c43a8eba22da)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
