# SXSW Twitter Sentiment Prediction

Authors: Ashli Dougherty, Cameron Tavares, Kelly Mullaney

## Overview

***
## Business Problem
#### How do attendees feel about our company and products? 
Each March thousands of people attend the [South by Southwest (SXSW)](https://www.sxsw.com/) conference in Austin, Texas. This event features sessions, music and comedy showcases, film screenings, exhibitions, professional development and a variety of networking opportunities. This past year (2011) we debuted the iPad2 and instituted a pop-up store at the festival. We analyzed posts from social media platforms such as Twitter to get real time feedback on what participants liked and disliked about their experience and our new products. Using these Tweets we can further circulate the positive feedback and take the negative comments to our customer service and product development teams in order to improve user experience.

***
## Data
### Data Understanding
Our data was obtained from [Dataworld.com](https://data.world/crowdflower/brands-and-product-emotions) as a CSV file. This dataset contained approximately 9,000 prelabled tweets collected from the 2011 SXSW attendees as either having a positive, negative, or neutral sentiment about Apple, Google, or one of their products, application, or conference sessions. 
 
### Data Exploration
First, when cleaning the data we decided to drop the following values due to the total number of tweets in the dataset: 
- duplicate tweets (118 tweets) 
- any tweets that had a classified sentiment of “I can’t tell’ (156 tweets)

Next, we created a function that binned the data into general companies –  Apple or Google. Any data point that could be classified was dropped as it would not give us usable feedback on our products or services. Next we examined the overall sentiments of all tweets of both Apple and Google. 

**INSERT GRAPH**

**Initial takeaways**: 
- Apple has more mentions than Google overall.
- Of Tweets that had a sentiment, 39% were positive and only 8% were negative. 
- When we compare this our competitor, only 30% were positive tweets, but Google had overall fewer negative tweets (5% of total mentions).

We furthered filtered the data to keep tweets that were only relevant to Apple, separated them by sentiment, and created word clouds that shows us the most relevelent words being used by participants. 

**Most Releant Positive Words**
INSERT CLOUD

**Most Releant Neutral Words**
INSERT CLOUD

**Most Releant Negative Words**
INSERT CLOUD

***
## Methods
Built a custom transformer that works in Pipeline:
    1. makes an X_copy for safety reasons
    2. makes str and lowercase
    3. tokenizes with default RegexTokenizer
    4. tags tokens with POS and converts POS to wordnet
    5. Lemmatizes with default WordNetLemmatizer
    6. creates corpus via ' '.join(X_copy)
    7. vectorizes via default TfidfVectorizer
    8. sparse matrix object

Used classification models that would predict the sentiment of the tweet based on text. Using the pipeline all of the following models were implemented with default parameters. Accuracy, precision, and F1 scores for all models were printed and compared. 
- Dummy Classifier
- Nearest Neighbors
- Linear SVM
- RBF SVM
- Decision Tree
- Random Forest
- Bagging
- Gradient Boosting
- Neural Net
- AdaBoost
- MultiNomial Naive Bayes

***
## Modeling
After an initial test, the top three performing models that will be grid searched for best parameters and compared again are: 
    1. RBF SVM –  accuracy: 66%, precision: 66%, f1: 62%
    2. Bagging – accuracy: 62%, precision: 64%,  f1: 61%
    3. Gradient Boosting: accuracy: 64%, precision: 65%, f1: 59%

**INSERT CONFUSIONS & RUCAUC**

***
## Evaluation 
Even after grid searching the best performing model was still RBF SVM with default parameters as seen in our **Modeling** section.  

The model seems to be labeling positive tweets as neutral. This may be from human error as near duplicate tweets in the dataset were labeled with opposing sentiments between the train and test sets. As the majority of tweets are neutral, the model may be overtrained on neutral sentiments. As we saw from the word clouds, neutral and positive tweets have a lot of token overlap and context can be hard to decipher. 


***
## Conclusions & Opportunites 
### Event Opportunities


### Product Opporunities 

***

## Limitations & Next Steps

***
### For more information: 
Please review our full analysis in our **LINK Jupyter Notebook** or our **LINK presentation**.

For any additional questions, please contact Cameron: tavarescameron1@gmail.com, Ashli: ashli.d.dougherty@gmail.com, or Kelly: mullaney.kelly.k@gmail.com 