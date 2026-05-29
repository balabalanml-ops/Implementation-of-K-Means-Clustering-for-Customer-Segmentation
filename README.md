# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the necessary packages using import statement.

2.Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().

3.Import KMeans and use for loop to cluster the data.

4.Predict the cluster and plot data graphs. 

5.Print the outputs and end the program.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by:Sri Bala Kumaran
RegisterNumber: 212225220104
*/

import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

# Load dataset
data = pd.read_csv("Mall_Customers (1).csv")

# Display basic information
print(data.head())
print(data.info())

# Check null values
print(data.isnull().sum())

# Elbow Method
wcss = []

for i in range(1,11):
    kmeans = KMeans(n_clusters=i, init='k-means++', random_state=42)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.figure(figsize=(8,5))
plt.plot(range(1,11), wcss, marker='o')
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

# K-Means with 5 clusters
km = KMeans(n_clusters=5, init='k-means++', random_state=42)
y_pred = km.fit_predict(data.iloc[:,3:])

# Add cluster column
data["cluster"] = y_pred

# Separate clusters
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]

# Plot clusters
plt.figure(figsize=(8,6))

plt.scatter(df0["Annual Income (k$)"],
            df0["Spending Score (1-100)"],
            c='black', label='Cluster 0')

plt.scatter(df1["Annual Income (k$)"],
            df1["Spending Score (1-100)"],
            c='cyan', label='Cluster 1')

plt.scatter(df2["Annual Income (k$)"],
            df2["Spending Score (1-100)"],
            c='yellow', label='Cluster 2')

plt.scatter(df3["Annual Income (k$)"],
            df3["Spending Score (1-100)"],
            c='blue', label='Cluster 3')

plt.scatter(df4["Annual Income (k$)"],
            df4["Spending Score (1-100)"],
            c='green', label='Cluster 4')

# Plot centroids
plt.scatter(km.cluster_centers_[:,0],
            km.cluster_centers_[:,1],
            s=200,
            c='red',
            marker='X',
            label='Centroids')

plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.title("Customer Segments")
plt.legend()
plt.show()



```

## Output:
<img width="724" height="136" alt="image" src="https://github.com/user-attachments/assets/099c7ac8-68db-474b-a74e-176e8dc9df46" />
<img width="553" height="120" alt="image" src="https://github.com/user-attachments/assets/fe5103cd-d4ba-4d7b-b2dc-4094340156b3" />
<img width="698" height="236" alt="image" src="https://github.com/user-attachments/assets/0214cafd-7cb8-4a1c-900d-86e9d8b6e1dd" />
<img width="934" height="576" alt="image" src="https://github.com/user-attachments/assets/2fdbe532-9513-4824-b9fd-83f45839fc89" />
<img width="953" height="681" alt="image" src="https://github.com/user-attachments/assets/7674782b-c565-4bd7-89f9-01dabeac3cf0" />


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
