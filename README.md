# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Choose the number of clusters (K).
2. Randomly initialize K centroids.
3. Assign each data point to the nearest centroid.
4. Recalculate the centroids.
5. Repeat steps 3 and 4 until centroids do not change.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Amrita B S
RegisterNumber:  212225100002
*/
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss= []
for i in range(1,11):
    kmeans=KMeans(n_clusters = i,init = "k-means++", random_state=42)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
plt.show()
km=KMeans(n_clusters = 5, init = "k-means++", random_state=42)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.figure(figsize=(10, 8))
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="black",label="Cluster 0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="cyan",label="Cluster 1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="yellow",label="Cluster 2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="Cluster 3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="green",label="Cluster 4")
plt.legend()
plt.title("Customer Segments")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.show()
```

## Output:
<img width="745" height="557" alt="image" src="https://github.com/user-attachments/assets/8fbcfc97-8693-4f66-8fbb-62d4c11ffdb0" />
<img width="849" height="699" alt="image" src="https://github.com/user-attachments/assets/02158120-36df-4bbf-9f5e-875b367bd154" />


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
