# COVID Twitter Vaccine NLP & KMeans Clustering

The purpose of this project is to gain insight on how people felt about a COVID-19 vaccine from the dates March 15, 2020 to May 15, 2020, a two month period. Thus, you can say this is a **Sentiment Analysis**. 

To achieve this, I utilized the **twitterscraper** library to scrape a sample of around **1000 tweets (1130 to be exact)** with known pro and anti-vaccine keywords and hashtags (pro, antivax, antivaxxer, vaccineswork, etc.). I then performed **NLP** on the text data within the tweet using **NLTK** and used **SciKit-Learn** to convert the text data into vectors using **TF-IDF (Term Frequency-Inverse Document Frequency)**. Lastly, I used **KMeans clustering** to get a broad sense of how much of the tweets could be pro-vaccine or anti-vaccine, or at least understand how often these terms are used in coronavirus vaccine related tweets. 

We begin with **collecting** the tweets and saving them to csv via twitterscraper. We then **clean/process** the data, dropping uneeded columns and performing NLP on the text within the tweets. We then do a brief **EDA (Exploratory Data Analysis)** on the processed text data by using TF-IDF. Finally, we **model** the data with KMeans, both our own implementation and the SKLearn one.

Credits to **Daniel Foley** from *Towards Data Science* on Medium for the article where the TF-IDF and KMeans code is based and to **Aman** from *Unfold Data Science* on YouTube for the tutorial on NLTK and NLP. Links to these sources are below:

K-Means Clustering: Making Sense of Text Data Using Unsupervised Learning: https://towardsdatascience.com/k-means-clustering-8e1e64c1561c

Text Data Cleaning in Python | How to clean text data in python: https://www.youtube.com/watch?v=KhXU7KOxQcg&t=4s
