# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. Import dataset and print head,info of the dataset
2. Check for null values
3. Import kmeans and fit it to the dataset
4. Plot the graph using elbow method
5. Print the predicted array
6. Plot the customer segments

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Thaksha Rishi
RegisterNumber:  212223100058
*/
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("Mall_Customers.csv")
print("Name: Thaksha Rishi")
print("Reg No: 212223100058")
df.head()
df.info()
df.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(df.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No.of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(df.iloc[:,3:])
y_pred = km.predict(df.iloc[:,3:])
print("Predicted values : ")
y_pred
df["cluster"] = y_pred
df0 = df[df["cluster"]==0]
df1 = df[df["cluster"]==1]
df2 = df[df["cluster"]==2]
df3 = df[df["cluster"]==3]
df4 = df[df["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer segments")
```

## Output:

<img width="670" height="432" alt="image" src="https://github.com/user-attachments/assets/f4ebdd96-d683-4b58-9983-c50ba5e22534" />

<img width="667" height="444" alt="image" src="https://github.com/user-attachments/assets/1d348fc2-25de-4ab0-9544-8737653c4368" />

<img width="644" height="441" alt="image" src="https://github.com/user-attachments/assets/72011f73-bfcf-4fe5-8ddf-59b1e68a4c2c" />


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
