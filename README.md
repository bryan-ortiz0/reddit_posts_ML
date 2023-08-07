# Web APIs & NLP 🍄

# Introduction:

Welcome to my NLP project focused on analyzing two distinct subreddits:

## **r/Psychonaut**
r/Psychonaut is a vibrant subreddit community that delves deep into the exploration of consciousness, psychedelic experiences, and spiritual topics. It serves as a platform for individuals interested in expanding their understanding of the mind, psychedelics, and the profound aspects of human existence

## **r/Microdosing**
On the other hand, r/Microdosing is a subreddit dedicated to the practice of microdosing. Microdosing involves the consumption of sub-percueptual doses of psychedelics, which means the doses are too small to induce hallucinations or alter perception significantly. This subreddit focuses on scientific research, informative discussions, and anecdotal reports related to microdosing benefits, protocols, and experiences.

Through our analysis, we aim to gain insights into the unique characteristics, discussions, and trends within these two communities, shedding light on the fascinating world of psychedelic exploration and microdosing practices.

# Project Overview:

This project aims to address this need by developing an accurate post classifier specifically tailored for the psychedelic community. By analyzing posts from two prominent subreddits, r/Psychonaut and r/Microdosing, we provide researchers, curious individuals, and enthusiasts with a valuable tool to gain insights into the diverse range of topics, discussions, and experiences shared within this community.

With this classifier, users will be able to explore and understand the nuances of each subreddit, uncovering valuable information about psychedelic exploration, spiritual insights, microdosing protocols, scientific research, and more. By delving deeper into the realm of human consciousness and psychedelic exploration, we hope to contribute to the broader understanding of these fascinating subjects.

## Data Collection (PRAW) and Cleaning

To develop an accurate post classifier for the psychedelic community, we utilized the PRAW (Python Reddit API Wrapper) package. PRAW facilitated seamless interaction with the Reddit API, enabling us to retrieve diverse data, including posts and comments.

With the aim of building a comprehensive dataset, we employed PRAW to gather posts from two prominent subreddits: r/Psychonaut and r/Microdosing. We explored various categories of posts, including *new*, *hot*, *top*, and *controversial*, ensuring a well-rounded representation of community discussions. This process yielded a substantial dataset of nearly **4000 posts for each subreddit**.

For each post, we collected essential information, such as the timestamp, title, and text. The timestamp was converted from coordinated universal time (UTC) to a more readable format, facilitating temporal analysis. Furthermore, we conducted thorough data preprocessing steps, addressing concerns such as duplicate posts, null values, and special characters within the post text. These measures ensured the quality and consistency of our dataset.

By leveraging the collected data, including the post titles and texts, we laid the foundation for training an accurate post classifier. These textual elements are key to capturing the essence of each post and extracting meaningful features necessary for classification

## Data Dictionary

| Name | Type | Description |
|------|------|-------------|
|**subreddit**|object|The subreddit from which a post was retrieved. It can be either "r/Psychonaut" or "r/Microdosing"|
|**timestamp**|datetime|The subreddit from which a post was retrieved. It can be either "r/Psychonaut" or "r/Microdosing"|
|**title**|object|The title of a post, which serves as description of the content|
|**text**|object|The main text or body of a post, providing detailed information, experiences, or discussions|
|**title_length**|int|The length of the post title, measured in characters|
|**text_length**|int|The length of the post text, measured in characters|
|**title_word_count**|int|The number of words in the post title|
|**text_word_count**|int|The number of words in the post text|
|processed_text|object|The preprocessed version of the post text, obtained after removing duplicates, null values, and special characters|
|target|int|The target variable indicating the classification label of a post. It is binary, with 0 representing "r/Microdosing" and 1 representing "r/Psychonaut"|

# Model and Results

To prepare the text data for modeling, a preprocessing step was performed, which involved removing stop words (commonly used words that do not carry significant meaning) and stemming words. Stemming is a technique used to reduce words to their root form, aiding in generalization and reducing the dimensionality of the data.

For modeling purposes, two algorithms were employed: **Random Forest** and **Naive Bayes**. These algorithms were coupled with two different vectorization techniques: **Term Frequency-Inverse Document Frequency (TF-IDF) Vectorizer** and **CountVectorizer**.

The TF-IDF Vectorizer calculates the importance of a word in a given text by considering both its frequency within the document and its rarity across the entire corpus. This approach helps to capture the relative importance of words within the context of the dataset.

On the other hand, the CountVectorizer simply counts the occurrences of each word in the text, disregarding their relative importance. This technique provides a basic representation of the textual data.

By utilizing these models and vectorization techniques, we can explore different aspects of the text data and assess the performance of the models in classifying posts from the two subreddits.

### Classification Report

|Model|Vectorizer|Precision|Recall|F1-Score|Support|
|-----|---------|----------|------|--------|-------|
|Random Trees (Psychonaut)|TfidfVectorizer|0.8577|0.8544|0.8560|522|
|Random Trees (Psychonaut)|CountVectorizer|0.8832|0.8544|0.8685|522|
|Naive Bayes (Psychonaut)|TfidfVectorizer|0.8738|0.8535|0.8635|430|
|Naive Bayes (Psychonaut)|CountVectorizer|0.8428|0.8977|0.8694|430|
|Random Trees (Microdosing)|TfidfVectorizer|0.8446|0.8480|0.8463|487|
|Random Trees (Microdosing)|CountVectorizer|0.8492|0.8789|0.8638|487|
|Naive Bayes (Microdosing)|TfidfVectorizer|0.8372|0.8594|0.8482|377|
|Naive Bayes (Microdosing)|CountVectorizer|0.8739|0.8090|0.8402|377|

### Test Score Accuracy
|Model|Vectorizer|Test Accuracy|
|------|--------|-------------|
|Random Forest|TfidfVectorizer|85%|
|Random Forest|CountVectorizer|87%|
|Naive Bayes|TfidfVectorizer|86%|
|Naive Bayes|CountVectorizer|86%|

# Conclusion

In conclusion, our project aims to provide valuable insights for researchers, curious individuals, enthusiasts, and the psychedelic community as a whole. To further enhance the accuracy and interpretability of our model, we recommend implementing lemmatization instead of stemming. This approach can help capture the nuanced meanings of words and improve the overall performance of the classifier.

Additionally, conducting sentiment analysis would be beneficial in distinguishing between positive and negative experiences shared within the psychedelic community. This analysis would provide valuable information about the sentiment and emotional tone of the posts, enabling a deeper understanding of the community's experiences and discussions.

Furthermore, exploring other models such as gradient boosting, support vector machines (SVMs), and neural networks could potentially yield even better results. These models have shown promising performance in various natural language processing tasks and may offer further insights and improvements to our classifier.

By incorporating these recommendations, we can continue to refine our classifier and provide more comprehensive and accurate insights for those interested in exploring the realm of human consciousness and psychedelic exploration.

Thank you for joining me on this journey of understanding and discovery.
