![](media/image1.png){width="3.893630796150481in"
height="1.658536745406824in"}

Fall -2018

BIA 660 C – Web Mining

Web Mining of Prescription Drugs Data for Market Study and Analysis

Prof. Rong Liu

Team 5

Gaurav Kshirsagar

Ajinkya Ingle

Priyanka Bhandari

Rohan Waghere

Team 5 Date: 12/07/2018

**Motivation**

The US has the largest pharmaceutical market in the world. If anyone
wants to buy a drug, he/she looks for the drug and its possible
side-effects in internet. WebMD is the largest website in terms of page
views and clicks. It is assumed to be a legitimate source of
information. We decided to scrape the data from the website regarding
the reviews posted by the patients or caretakers on the website. It will
give us a good overview of a particular drug if we get the sentiment
analysis and frequently cited side-effects in the reviews. It can also
provide valuable information regarding the competitors drugs which are
mentioned in the comments.

**Introduction **

The US has the largest pharmaceutical market in the world with a value
of \$339 billion USD. US prescription drug spending is expected to reach
as high as \$610 billion by 2021. Pfizer alone spent 7.6 billion dollars
on R&D in financial year 2017. The growth is expected to accelerate in
coming years. While these drugs are prescribed for their therapeutic
properties, their use may result in unintended or adverse effects. There
is a need for people to know the quality of drugs in this overcrowded
market.

**Project Plan**

![](media/image2.png){width="6.586021434820648in"
height="2.5520833333333335in"}

Sheet was edited online and hence is signed digitally.

We started to work according to the above-mentioned plan gathering and
cleaning the data. In later stages we were able to get some initial EDA
done. At last we were working on classification models and LDA Topic
modeling concepts to look for useful insights.

1.  **Scrapping the Data**

    We first started with going through the WebMD webpages to look for
    the data we needed. We were looking for some specific category of
    drugs to be investigated. Finally, we decided to study chronic pain
    diseases.

Home page of WebMD

> ![](media/image3.png){width="6.5in" height="3.5833333333333335in"}
>
> After searching for ‘Chronic Pain’ we got the following results.
>
> ![](media/image4.png){width="5.170833333333333in"
> height="2.988170384951881in"}

We obtained the top 5 drugs ranked by the number of reviews. And later
we collected data from all of them one by one to do a comparative study.

The review format looked like the following picture

![](media/image5.png){width="6.5in" height="2.982638888888889in"}

The PHP source code was a below.

![](media/image6.png){width="6.5in" height="3.740972222222222in"}

Every page had at max 5 comments. So, we had to go through 200-300 pages
to mine all of the 2500-3500 reviews and rating from the website.

1.  **Cleaning the data**

    The data initially had a lot of noise which needed to be cleaned. We
    removed any repetitive words from the comments. We also segmented
    the reviewer information in different column like “age” and
    “gender”.

    Following is the image of raw scrapped data

> ![https://lh6.googleusercontent.com/1n6EkSBtepbCzWLNc2YlLHx-xqISPWDEY59I9qMoAtIKkuX1sN03y\_K0uQByj6nYyubpBaKoU0WpZyiYPpohxLt8zpc3mbVjyU7dRb\_Nl\_oM-El0phMvLhrWM-EBlQvTnlZWZWqiOkQ](media/image7.png){width="5.385416666666667in"
> height="2.426314523184602in"}

After the preprocessing and cleaning we had this data to work with.

> ![https://lh5.googleusercontent.com/RYAT6Okzgriq0sAGYV3W8zOUqinOSlDEP0BObsXDL5ENC0sytX-GWVeEDUQX31iAjdS6DU\_CSAjxB0kfL3ow4oPYvWbLzHr7nj1xbP6UFl7oJ3WjHlGAsEdDsbVQ88BnspYX6YsOpZI](media/image8.png){width="5.805637576552931in"
> height="3.1354166666666665in"}

1.  **EDA – Exploratory Data Analysis**

    In EDA we have observed some really unusual patterns which we have
    discussed in detail in the following sections. There were variable
    reactions to this drug in various age groups across males and
    females.

![](media/image9.png){width="3.6354166666666665in"
height="2.8125in"}***EDA: Gender***

***EDA: Age***

![](media/image10.png){width="5.114583333333333in"
height="3.704861111111111in"}

***EDA: Effectiveness Rating***

![](media/image11.png){width="5.080680227471566in"
height="3.705051399825022in"}

***EDA: Satisfaction Ratings***

![](media/image12.png){width="5.0625in" height="3.7045384951881015in"}

***EDA: Comparing two or more features***

![](media/image13.png){width="5.083333333333333in"
height="3.4819444444444443in"}

***EDA: Comparing two or more features***

![](media/image14.png){width="4.416666666666667in" height="2.5in"}

![](media/image15.png){width="5.135416666666667in"
height="3.5729166666666665in"}

1.  **NLP and Reviews analysis**

    It was observed that most of the reviews in our sample dataset were
    rated 1,4 or 5

    Also, the length of most of the review never exceeded 50 words.

![https://lh3.googleusercontent.com/ayjrnpzJdI5TZvaqRt5u0oLi2s9t9MM4NUgFXIs5z7zjMixbgbh8pvRz0Ry\_AHIvooKgJG9EteNxlr5V9vgjQ9RV1bsbjFktM0l0t8r1HrSTPyZ55H6XwH0ZFX\_wHA8pLEhlbOFVKmM](media/image16.png){width="6.5in"
height="3.486111111111111in"}

![https://lh4.googleusercontent.com/NIXKTNj3TNoA7qhwqFlMQANGZ9MSCkSuuZggxwKAjmyx6P5CQBcOdziF\_YALgaf87Rsp6BgSfOivJBHEISJkc6k\_S9OxF8mQHEJhKdnvsbpmXQ9pjn7TRVJHLomkgL9RdWlp5hUOYjQ](media/image17.png){width="6.5in"
height="3.611111111111111in"}

We also calculated the review length to rating **correlation** to be
**0.068**

Using tfidf vectors we determined the top 5 words by their weight,
occurring in every comment. This gave us a brief idea of what people
were taking about in the comments.

> ![](media/image18.png){width="6.745657261592301in"
> height="2.3645833333333335in"}

We were also able to spot some side effects in these extracted top5
words by tfidf weight.

Wordclouds made it easier to spot the keywords we were looking for.

***Wordcloud for Male patients***

![](media/image19.png){width="6.5in" height="3.2354166666666666in"}

***Wordcloud for Female patients***

![](media/image20.png){width="6.5in" height="3.2354166666666666in"}

1.  **Classification**

    We used 2 approaches to classification.

<!-- -->

a)  Extract Features from the comments and use these features as input
    parameters to classify the satisfaction rating.

b)  Tokenize the comments, generate tfidf vectors and then classify
    satisfaction ratings based on the on these vectors.

***First Approach***

We used 3 buckets of comments for an extended study of classification.
We used:

-   Comments

-   Cleaned Comments and

-   Adjectives from the comments

Results

![https://lh3.googleusercontent.com/PqCMGaFgWNh2m7swsmxlWQ1oTizLTytys83XbbnBmYtRBwy33Srn-lurS1ev3QcKpgCYSWjN7G1w0UNyTF5dThyCwgrUq3glyBW59cx\_zAgCffMZPJPmNdnnfmoXj03tpOfi3kL0UBU](media/image21.png){width="4.21923009623797in"
height="3.7576388888888888in"}

***Second Approach***

We are using following steps to perform classification.

-   Download the data in csv format

-   Adding number of words, punctuations, unique words, stop words.

-   Introducing polarity and subjectivity with the help of Text Blob and
    to see if performance can be improved.

-   Run various models including Naive Bayes, KNN, Neural Networks,
    Random Forest, Logistic Regression, SVM.

-   Calculate their accuracies and compute confusion matrix for each and
    then compare.

-   Then we perform parameter tuning on Neural Network algorithm which
    yields us 50 % total precision.

    ![](media/image22.png){width="6.5in" height="5.354166666666667in"}

**Naïve Bayes**:

-   This text-based classification algorithm assumes that words in a
    document are independent hence the performance achieved was not
    appropriate as it does not model the text well

<!-- -->

-   Satisfaction rating was predicted with respect to other numeric
    columns in the dataset. After fitting the algorithm, we achieved
    model accuracy of 59%.

-   In confusion matrix, the diagonal items represent true-positive
    values whereas everything else either represents true-negative or
    false-positive values. This corresponds to error of 41%.

**Parameters and confusion matrix**

![](media/image23.png){width="4.104166666666667in"
height="1.4628718285214348in"}

**Logistic Regression Algorithm**:

-   We have taken 100 iterations to achieve appropriate accuracy and to
    make the model optimize our performance since our dataset was not
    really big , thus this algorithm couldn’t prove to be that
    significant for our use.

<!-- -->

-   We achieved model accuracy of 60.6%.

-   In confusion matrix, the diagonal items represent true-positive
    values whereas everything else either represents true-negative or
    false-positive values. This corresponds to error of 39.4%.

**Parameters and confusion matrix**

![](media/image24.png){width="6.5in" height="1.6715277777777777in"}

**Support Vector Machine Classifier Algorithm**:

-   Satisfaction rating was to be predicted with respect to other
    numeric columns in the dataset. After fitting the algorithm, we
    achieved model accuracy of 43%.

-   In confusion matrix, the diagonal items represent true-positive
    values whereas everything else either represents true-negative or
    false-positive values. This corresponds to error of 57%.

**Parameters and confusion matrix**

![](media/image25.png){width="6.5in" height="1.8569444444444445in"}

**Random Forest Algorithm: **

-   It’s a very popular classifier used to fit the model as it helps to
    combine multiple models ie multiple decision trees to achieve the
    results

<!-- -->

-   Satisfaction rating was predicted with respect to other numeric
    columns in the dataset. After fitting the algorithm, we achieved
    model accuracy of 61.6%. It proved to be a good predictor variable
    for our case.

-   In confusion matrix, the diagonal items represent true-positive
    values whereas everything else either represents true-negative or
    false-positive values. This corresponds to error of 38.4%.

**Parameters and confusion matrix**

![](media/image26.png){width="6.5in" height="2.1506944444444445in"}

Steps followed for Random Forest:

**Neural Network Algorithm**: Satisfaction rating was predicted with
respect to other numeric columns in the dataset. After fitting the
algorithm, we achieved model accuracy of 59.3%.

In confusion matrix, the diagonal items represent true-positive values
whereas everything else either represents true-negative or
false-positive values. This corresponds to error of 40.7%.

**Parameters and confusion matrix**

![](media/image27.png){width="6.5in" height="2.0868055555555554in"}

**K-Nearest Neighbors Algorithm:** Satisfaction rating was predicted
with respect to other numeric columns in the dataset. After fitting the
algorithm, we achieved model accuracy of 40%.

In confusion matrix, the diagonal items represent true-positive values
whereas everything else either represents true-negative or
false-positive values. This corresponds to error of 60%.

**Parameters and confusion matrix**

![](media/image28.png){width="6.5in" height="1.6743055555555555in"}

**Comparison of all Classification Algorithms:**

![](media/image29.png){width="5.4375in" height="3.219511154855643in"}

Hence, we found that Random Forest algorithm aligns with the data and
proved to be a better classifier for our dataset.

**Parameter Tuning**: We performed Grid search on Neural Network
algorithm which yielded us a average precision of 50%, although there
were no significant performance improvement was observed.

![https://lh5.googleusercontent.com/WbhyTcxwylwizjcdamuoFYkR414g1RbRqf7TRMLIFYuikTr\_umgr1YOqbPh5KCfRzjCpwmjHxbNBf7soSWm08MBJCH02ji5vOhxBdsJq3IB8dh7YsL8la3JIDp2jmQXNbehgAAqkdAQ](media/image30.png){width="5.4375in"
height="1.1770833333333333in"}

![https://lh4.googleusercontent.com/eOkyi3fsij7lR\_31anEci8U1dkpaxMgekee1sWQ-UVh9xiUawNAL0ZgF4-KjPCjdBorLeaHm46HPDu5-jdYaUGenzau4\_SuqI38wMGZG0AZETfRrSqPshLqu2a\_KZZLRnfe2s6fSleI](media/image31.png){width="4.885416666666667in"
height="1.9781758530183726in"}

1.  **LDA Topic Modeling**

    Performed LDA topic modeling on our dataset to look for abstract
    topics that might occur in the collection of document

    LDA without tfidf

    ![](media/image32.png){width="6.5in" height="2.6694444444444443in"}

    LDA with tfidf

    ![](media/image33.png){width="6.5in" height="1.8097222222222222in"}

-   **1st topic** mentions the positive words, it means it works for a
    fair amount of customers

-   **However, 2nd Topic** shows the side effects like “**Dizziness**”
    and “**Itching**”

-   Also, People who need more potent drugs use “**Vicodin**” instead of
    “**Tramadol**”

-   **Fibromyalgia** is widespread muscle pain in back and shoulder.
    That one of the reason patients are prescribed Tramadol to **reduce
    pain**

    **6. Sentiment Analysis**

    We found that most of the comment were negative and subjective

    ![](media/image34.png){width="6.5in" height="3.3180555555555555in"}

1.  **Comparative analysis with other drugs**

Different age groups have a different pattern of side-effects. Just by
observing the graph is becomes much clear that the drugs have different
side-effects across the age groups. It is also affected by the gender of
the patients.

![](media/image35.png){width="4.989583333333333in"
height="1.9958333333333333in"}

![](media/image36.png){width="4.999006999125109in"
height="1.9269674103237096in"}

![](media/image37.png){width="4.97628280839895in"
height="2.2754811898512686in"}

**Conclusion and Future work:**

-   WebMD reviews are not the ideal place for drug companies to look for
    insights since people are inherently **biased** either along a
    positive side or a negative one.

-   However, it is a good source to know the customers **sentiments**,
    the **drug side-effects** and study **competitor’s** drugs.


