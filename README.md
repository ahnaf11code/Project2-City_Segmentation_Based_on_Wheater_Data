# Project2-City_Segmentation_Based_on_Weather_Data
The dataset contains several informations about city's weather condition in the day. Every city has their own characteristic based on their weather condition. So we can group them in the several clusters and knowing what is each clusters characteristic. From those characteristics, we can predict whether that city will get snowing or not. But domain of this project is just to define the clusters.

First step for doing machine learning or any data science problem is to define WHAT QUESTION SHOULD I ANSWER FROM THIS PROJECT. So I define some questions that will be answered. The questions are:
1. How many number of cluster ?
2. How's the characteristic of each cluster?

The dataset is splitted up into 2 part; train and test. This project is only use TRAIN data, so if I mention "dataset", it's equal to TRAIN data.
The dataset has 24 features and 109.095 rows. It's imposible to show the dataset here. This dataset contains several rows with missing values

![image](https://user-images.githubusercontent.com/82840840/116866588-dc0cc280-ac35-11eb-9957-48391accb750.png)

Very firstly, we drop some columns that will not be used in calculation process. Those columns are "id, Tanggal, KodeLokasi, BersaljuHariIni, BersaljuBesok"

Remember we have rows with missing values, so we have to deal with it. Maybe the first thing that coming out your mind is to DROP all rows with missing values. It's not wrong, but you can't do that. Missing values is almost a half of the dataset, so if we drop those rows, we'll lose a lot of information. Before we decide what we have to do, let's take a look on correlation matrix from the data (note: just ignore the deleted columns)

![image](https://user-images.githubusercontent.com/82840840/116867275-0612b480-ac37-11eb-8ffc-1a4430369a11.png)
![image](https://user-images.githubusercontent.com/82840840/116867301-1165e000-ac37-11eb-9f7b-2d1a2e7a9d72.png)

As we can see, every variables has correlation to each other. So we can impute the missing values with regression from others rows. 
After doing a regression we got

![image](https://user-images.githubusercontent.com/82840840/116867491-8afdce00-ac37-11eb-9eff-43227d6f61af.png)

Hold on !!! there's still 3 features have missing values. Don't worry, regression is only act to continues variables, those 3 variables are categorical features.
Now we're dealing with missing categorical values. First, I think that I can implement classification method to impute them, but the accuracy is very low, only 15%. So I decide to cluster the data WITHOUT 3 variables, then I impute the mode of each variables to missing categorical values. 
So now, we got 0 missing values

![image](https://user-images.githubusercontent.com/82840840/116870373-addeb100-ac3c-11eb-8c24-4636fb2fd35a.png)

The data is almost ready to clustered, but there's one thing to do, we have to standardize the data

![image](https://user-images.githubusercontent.com/82840840/116870503-e088a980-ac3c-11eb-832f-feda6d0d0ed5.png)

The data is now clearly ready to clustered. Method that used is KMeans clustering. First we define the number of K (optimum number of clusters)

![image](https://user-images.githubusercontent.com/82840840/116870641-1168de80-ac3d-11eb-9b32-9feed1ebcf3a.png)

With elbow method, we can decide K=5. 
So after that we calculate KMeans, and we got 5 clusters (cluster_0, cljuster_1, cluster_2, cluster_3, and cluster_4). The characteristic of each clusters are 
Cluster_0
![image](https://user-images.githubusercontent.com/82840840/116870869-82a89180-ac3d-11eb-85ba-dab7c8f0421d.png)

Cluster_1
![image](https://user-images.githubusercontent.com/82840840/116870932-a370e700-ac3d-11eb-9267-711237c922f8.png)

Cluster_2
![image](https://user-images.githubusercontent.com/82840840/116870966-b2f03000-ac3d-11eb-9e53-e00cda336aef.png)

Cluster_3
![image](https://user-images.githubusercontent.com/82840840/116871003-bf748880-ac3d-11eb-9b93-3cdf17bfc911.png)

Cluster_4
![image](https://user-images.githubusercontent.com/82840840/116871040-cd2a0e00-ac3d-11eb-9630-9269295f743f.png)




