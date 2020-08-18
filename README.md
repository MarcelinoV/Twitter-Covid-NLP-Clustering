# COVID Twitter Vaccine NLP & KMeans Clustering: Project Overview

The purpose of this project is to gain insight on how people felt about a COVID-19 vaccine from the dates March 15, 2020 to May 15, 2020, a two month period. Thus, you can say this is a **Sentiment Analysis**. 

To achieve this, I utilized the **twitterscraper** library to scrape a sample of around **1000 tweets (1130 to be exact)** with known pro and anti-vaccine keywords and hashtags (pro, antivax, antivaxxer, vaccineswork, etc.). I then performed **NLP** on the text data within the tweet using **NLTK** and used **SciKit-Learn** to convert the text data into vectors using **TF-IDF (Term Frequency-Inverse Document Frequency)**. Lastly, I used **KMeans clustering** to get a broad sense of how much of the tweets could be pro-vaccine or anti-vaccine, or at least understand how often these terms are used in coronavirus vaccine related tweets. 

We begin with **collecting** the tweets and saving them to csv via twitterscraper. We then **clean/process** the data, dropping uneeded columns and performing NLP on the text within the tweets. We then do a brief **EDA (Exploratory Data Analysis)** on the processed text data by using TF-IDF. Finally, we **model** the data with KMeans, both our own implementation and the SKLearn one.

Credits to **Daniel Foley** from *Towards Data Science* on Medium for the article where the TF-IDF and KMeans code is based and to **Aman** from *Unfold Data Science* on YouTube for the tutorial on NLTK and NLP. Links to these sources are in the Code and Resources.

## Code and Resources Used

**Python Version**: 3.6

**Packages**: TwitterScraper, nltk, pandas, numpy, matplotlib, seaborn, sklearn, datetime, re, string

**TwitterScraper Page**: https://github.com/taspinar/twitterscraper

**K-Means Clustering: Making Sense of Text Data Using Unsupervised Learning**: https://towardsdatascience.com/k-means-clustering-8e1e64c1561c

**Text Data Cleaning in Python | How to clean text data in python**: https://www.youtube.com/watch?v=KhXU7KOxQcg&t=4s

## Data Collection
Used the TwitterScraper package to query tweets with keywords such as vaccine, coronavirus, covid, antivax, pro, and others.
With each user tweet came the following information:
- Tweet-id
- Tweet-url
- Tweet text
- Tweet html
- Links inside Tweet
- Hashtags inside Tweet
- Image URLS inside Tweet
- Video URL inside Tweet
- Tweet timestamp
- Tweet Epoch timestamp
- Tweet No. of likes
- Tweet No. of replies
- Tweet No. of retweets
- Username
- User Full Name / Screen Name
- User ID
- Tweet is an reply to
- Tweet is replied to
- List of users Tweet is an reply to
- Tweet ID of parent tweet

## Data Cleaning

After collecting the data, I cleaned up the text data through NLP/text processing to make it usable for clustering. I did the following:
- Remove unneeded columns such as screen name, username, user id, tweet id, etc. In short, everything except **timestamp,	text,	hashtags,	likes,	retweets**
- Checked for duplicates in the data (there were none)
- Changed the data type of timestamp to datetime
- Performed lowercase conversion on the hashtag column
- Performed NLP/ text processing on text column
  - Lowercase Conversion
  - Tokenization
  - Puctuation/Twitter Character Removal
  - Stopword Removal
  - Stemming and Lemmatization 
  - Web Term Removal 
  
## EDA
 
Found that top 20 most frequent words in data set included antivaxxer, coronavirus, flu, vaccination, and other words. Also found tha both pro and antivax were on average found in about **11.5%** of our tweets with a near identical standard deviation, and terms like coronavirus and covid19 were on average found in about **21-22%** of the dataset.

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/top_feats_desc.JPG "Descriptive Stats of Top 20 Words")

## Model Building 

First I created a KMeans class to developt a deeper understanding of how the algorithms work, and then used both the class and the sklearn equivalent to group the tweets by KMeans. The resulting graphs are basically the same except for different color coding.

Own Implementation:

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/own_kmeans.JPG "Class Implementation of KMeans Algorithm")

Sci-Kit Learn Implementation:

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/sklearn_kmeans.JPG "SKLearn Implementation of KMeans Algorithm")

I then investigated using different clustering algorithms on the data to see if any method grouped the data differently. I used:

- Mini-Batch KMeans

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/mini_batch_kmeans.JPG "Mini-Batch KMeans Clustering")

- Spectral

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/spectral.JPG "Spectral Clustering")

- Gaussian Mixture Models

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/gaussian.JPG "Gaussian Mixture Models Clustering")

Out of all of these, GMM grouped the data points differently than KMeans, giving more weight to the left-most cluster.

## Model Analysis

I used the **Elbow Method** to determine if the optimal number of clusters to use which came out to be **3.** The optimal number is determined from where the elbow **bends**.

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/elbow.JPG "Elbow Method")

I then visualized the 3 clusters into separate graphs to view which terms each cluster consists of. The clusters that both KMeans and Gaussian generated were divided by "pro", "vaccine", and "antivax" terms, with the antivax cluster having the most significant different in term distribution.

KMeans Antivax Cluster:

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/"kmeans antivax".JPG "KMeans antivax")

Gaussian Antivax Cluster:

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/"gaussian antivax".JPG "Gaussian antivax")

Cluster Feature Plots:

**KMeans**

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/kmeans_dfs.JPG "KMeans feat plot")

**Gaussian Miture Models**

![alt text](https://github.com/MarcelinoV/Twitter-Covid-NLP-KMeans/blob/master/Images/gaussian_dfs.JPG "GMM feat plot")
