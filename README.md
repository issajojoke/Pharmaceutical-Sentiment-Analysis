# Pharmaceutical-Sentiment-Analysis

## Project Outcomes
For this project, I created a sentiment analysis on pharmaceutical drugs reviews using NLP (natural language processing) to classify and predict satisfaction ratings out of ten. The goal for this is to be able to maintain and stay updated on medication integrity, safety, and satisfaction.
 
The modules used in this project include: pandas, sklearn, collections, numpy, csv, ast, joblib, nltk, BERT, tensorflow, keras

## Problem
When a patient is newly prescribed a medication that they are unfamiliar with, they tend to take it to the internet. They will post on google, twitter, reddit, etc. with the goal of gaining some insight from other patients who are on the same medication. How their experience has been with the medication, the pros, the cons, if they've tried other alternatives and if those have been suitable for them. Many questions can be answered in those discussion forums. 
As a data scientist on a pharmaceutical data team, it would be very beneficial to monitor the key words used in these discussion forums to have a deeper understanding of how these medications are benefitting the patients, and what may need improvement. 

### Process
1. Find the proper dataset - A data set was found on kaggle and has 161298 rows of data, containing the uniqueID, drug name, condition, review, raiting, and usefulcount was chosen for this project.
2. Data cleaning/preprocessing - Cleaned and normalized the text in all columns with text by replacing random characters, making all text lowercase, tokenizing, removing stopwords, and stemming the text. Completed this using CountVectorizer from sklearn. Then inserted the key words from all reviews as a list in a new column.
3. Exploratory data analysis - Looked at the statistics of the numeric values for rating and usefulCount. Got a description of the average rating/usefulCount, and the average length of reviews.
    - created a new dataframe with 2 columns; ratings, combined words (combined all words associated with the same rating)
    - took top 200 words from each list
4. Feature engineering - converted the top 2000 words list and the words list in the dataframe into matching numeric values using bag of word (CountVectorizer)
    - counted how many times a word showed up for each rating to compare frequency 
    - balanced the data by using the oversampling method by replicating minority data.  
5. NLP preparation - Convert words to a numeric representation using BagOfWords through CountVectorizer. Also used DistilBert to account for context and nuance. 
    - Due to difficulty with accurately predicting the numeric ratings (1-10), I opted for a more accurate approach by splitting the ratings into 3 separate classes. This allowed for less errors. 
6. NLP modelling - Used numerous models to determine which model is the most accurate: naive bayes, SVM classification models, keras neural network models. 
7. Finalize sentiment analysis model 

### Findings
- In my case, support vector machines are the most accurate models for text classification.
- Using the DistilBert language model actually decreased my accuracy scores in all of my models; classification, and neural networks. 
    - Could be due to mismatched data when the classification models were fed the scores. 
- Working with medical text data requires lots of additional considerations. Such as medical jargon, medication names, etc., resulting in a more complex classification problem. 

### Challenges
- Finding a topic and appropriate dataset. I had so many ideas but not enough data, or I found a really clean dataset, but wasn't interested enough in the content.
- During data cleaning, because of the size of the dataset, it took a very long time to execute my steps. I had to learn how to utilize parallel processing by using joblib to optimize my program.
- During the data preparation, I was trying to extract the top 200 words from each list, but I kept getting a list of words separated by its characters. It came to my attention that my column was not properly formatted. It was formatted as: '[][][][][]' instead of: '[]'. I fixed this using literal_eval to have it check the objects, ensuring it was a list and not a string before flattening the list. 
- Making the model more accurate - learned about different models to come up with a more accurate classification model, eg. BERT. 
- Dealing with imbalanced data - 89%% of ratings were above 5/10, and the average of all drugs was 7.75/10
    - attempted to utilize SMOTE in order to artifically create new data with lower ratings, however it was incompatible with my version of python
    - due to time constraints, I decided to go with a more simple approach to data balancing - oversampling (sampling with replacement)
- Building neural network models is quite difficult to grasp and understand. I spent a lot of time learning how to effectively build them. 
- Optimization of the programs. A lot of time was required to execute the majority of my code, I had to learn how to configure the programs to be more efficient using parallel processing (joblib).

### If I had more time 
- Experiment and find ways to make the model more accurate. 
    - Explore more methods on balancing data.
- Utilize a medical corpus to account for medical jargon in the text reviews.
