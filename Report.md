# WebMD Data Mining Project - Report

### Motivation
  The US has the largest pharmaceutical market in the world. If anyone wants to buy a drug, he/she looks for the drug and its possible side-effects in internet. WebMD is the largest website in terms of page views and clicks. It is assumed to be a legitimate source of information. We decided to scrape the data from the website regarding the reviews posted by the patients or caretakers on the website. It will give us a good overview of a particular drug if we get the sentiment analysis and frequently cited side-effects in the reviews. It can also provide valuable information regarding the competitors drugs which are mentioned in the comments.

### Introduction
  The US has the largest pharmaceutical market in the world with a value of $339 billion USD. US prescription drug spending is expected to reach as high as $610 billion by 2021. Pfizer alone spent 7.6 billion dollars on R&D in financial year 2017. The growth is expected to accelerate in coming years. While these drugs are prescribed for their therapeutic properties, their use may result in unintended or adverse effects. There is a need for people to know the quality of drugs in this overcrowded market.

### 1.	Scrapping the Data
  We first started with going through the WebMD webpages to look for the data we needed. We were looking for some specific category of drugs to be investigated. Finally, we decided to study chronic pain diseases. 
 * We obtained the top 5 drugs ranked by the number of reviews. And later we collected data from all of them one by one to do a comparative study.
 * Every page had at max 5 comments. So, we had to go through 200-300 pages to mine all of the 2500-3500 reviews and rating from the website.
 
### 2.	Cleaning the data
  The data initially had a lot of noise which needed to be cleaned. We removed any repetitive words from the comments. We also   segmented the reviewer information in different column like “age” and “gender”. 

### 3.	EDA – Exploratory Data Analysis
  In EDA we have observed some really unusual patterns which we have discussed in detail in the following sections. There were   variable reactions to this drug in various age groups across males and females.

 * Using tfidf vectors we determined the top 5 words by their weight, occurring in every comment. This gave us a brief idea of what people were taking about in the comments.
 * We were also able to spot some side effects in these extracted top5 words by tfidf weight.
 * Wordclouds made it easier to spot the keywords we were looking for.

### 5.	Classification
 We used 2 approaches to classification.
 * a)	Extract Features from the comments and use these features as input parameters to classify the satisfaction rating.
 * b)	Tokenize the comments, generate tfidf vectors and then classify satisfaction ratings based on the on these vectors.

  #### First Approach

  We used 3 buckets of comments for an extended study of classification. We used:
  *	Comments
  *	Cleaned Comments and
  *	Adjectives from the comments

  #### Second Approach

  We are using following steps to perform classification.
  *	Download the data in csv format 
  *	Adding number of words, punctuations, unique words, stop words.
  *	Introducing polarity and subjectivity with the help of Text Blob and to see if performance can be improved.
  *	Run various models including Naive Bayes, KNN, Neural Networks, Random Forest, Logistic Regression, SVM. 
  *	Calculate their accuracies and compute confusion matrix for each and then compare.
  *	Then we perform parameter tuning on Neural Network algorithm which yields us 50 % total precision.

  **Parameter Tuning:** We performed Grid search on Neural Network algorithm which yielded us a average precision of 50%, although   there were no significant performance improvement was observed.
  
### 6.	LDA Topic Modeling
  Performed LDA topic modeling on our dataset to look for abstract topics that might occur in the collection of document
  *	1st topic mentions the positive words, it means it works for a fair amount of customers 
  *	However, 2nd Topic shows the side effects like “Dizziness” and “Itching”
  *	Also, People who need more potent drugs use “Vicodin” instead of “Tramadol”
  *	Fibromyalgia is widespread muscle pain in back and shoulder. That one of the reason patients are prescribed Tramadol to   reduce pain

### 7.	Comparative analysis with other drugs
  Different age groups have a different pattern of side-effects. Just by observing the graph is becomes much clear that the     drugs have different side-effects across the age groups. It is also affected by the gender of the patients.

### Conclusion and Future work:

  *	WebMD reviews are not the ideal place for drug companies to look for insights since people are inherently biased either along a positive side or a negative one.
  *	However, it is a good source to know the customers sentiments, the drug side-effects and study competitor’s drugs.
