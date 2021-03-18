# Project 3: Analyzing Subreddits with NLP and Classifiers
**Submitted by: Melody Wu**  
**March 5, 2021**

<img src="./image/cover_pic.jpg" style="height: 300px">

[Image source](https://media.sproutsocial.com/uploads/2020/08/Insights_Blog_Reddit-01.svg)  

This README serves as the executive summary of this project.

---
## Contents  
The rest of the report is organized as below:  
1. Introduction Problem Statement - *in this current file*
2. Data Collection and Pushshift - *in the Data Collection notebook*
3. Sentiment Analysis - *in the Data Collection notebook*
3. Exploratory Data Analysis (EDA) - *in the EDA and modeling notebook*
4. Modeling and Evaluation - *in the EDA and modeling notebook*
5. Misclassification Analysis - *in the EDA and modeling notebook*
7. Conclusions and Recommendations - *in this current file*
---


## Introduction and Problem Statement

Different people have different financial goals during different life stages:
- Some people might have born with a trust fund or they can make a ton to have money to save and invest.
- Some others just live paycheck-by-paycheck or even relying on borrowings and credits. These people rarely have anything to save or to invest. They should pay off their debts before investing.
- Many others indeed have debts even before they start their first jobs. According to [Investopedia](https://www.investopedia.com/student-loan-debt-2019-statistics-and-outlook-4772007), on average college grads in U.S. start their career with $37,584 in student loan debts.

Whether to pay back the debt or to invest the free cash is a difficult and complex question for most of the people. According to many experts, the answer to this question is 'it depends'. According to [Investopedia](https://www.investopedia.com/articles/pf/08/invest-reduce-debt.asp), individuals have to consider many different factors (e.g., return on investment vs. cost on loans) in order to make a good decision, and in fact, many of us do not make wise decision in terms of our personal finance. In addition, it is also noticed that personal finance decisions (regardless paying debts or investing) can be stressful and sometimes can take one's life. Therefore, it is important for open discussion platforms, like Reddit, to incorporate some monitoring and flagging features to help the users.

The problem this project hopes to solve is to classify texts that were written by zero debt-achievers (people who have debts and they are currently trying to pay off their debts) or by investors (people who have money to investor and hope to make a returns from investments). The first goal is to analyze and classify these texts (from Reddits, blogs, and other social media). Second, based on the classification, advice, supports, and relevant information (such as finance companies advertisements, finance education, FinTech Apps) can be recommended to the writers of the information and the viewers.

In this project, posts from thre subreddits were collected:
- [r/debtfree](https://www.reddit.com/r/debtfree/)
- [r/Debt](https://www.reddit.com/r/Debt/)
- [r/investing](https://www.reddit.com/r/investing/)

All these three subreddits were used is the sentiment analysis, but only r/debtfree and r/investing are used for the modeling, because I want to use a binary classifier and the r/debtfree subreddit is more similar to r/investing, thus giving more challenge to the model.


### Dataset
Using Pushshift APIs, 500 posts (titles only) from each of the subreddits (r/debtfree and r/investing) were collected, making balanced sample of a total observation of 1000 observations. Comments to the original posts were not collected. There is also no restrictions applied to the time range, these samples were collected from recent. There is no randomization done in the sample.

## Sentiment Analysis
By conducting a sentiment analysis here, I hope to see how sentiment distributes through different subreddit posts. The ultimate goal is flag people with extreme low sentiment and intervene with mental help support and a next-level review of the content. For the investing community, having too high sentiment could be problematic as well, as people feel extremely happy and overconfident, their risk tolerant might increases and they might expose themselves to risks that they would not normally take.

The sentiment analysis confirms my hypothesis that texts on investing are generally more positive. Also, both groups have shown extreme negative and positive texts and they alert us that it is necessary to provide mental health support to our users.   

Reference:
https://www.aeaweb.org/articles?id=10.1257/jep.21.2.129

## EDA
The most important takeaway from EDA is that "help", "advice", and "need" are the top most occurring text for r/debtfree, indicating that these users desperately need help for their personal finance. Thus, it is meaningful to partner with financial advising companies to help our users. For the r/investing subreddit, frequent discussion of "crypto" and "trading" indicate that our users are more like speculators than long-term investors. Therefore, financial advice is also needed for this group.   

## Model Development and Evaluation
Using pipeline and GridSearch, the production model selected is a Support Vector Model with TF-IDF Vectorizer with the below hyperparameters:

```python
{'svc__C': 1.0,
 'svc__degree': 2,
 'svc__kernel': 'rbf',
 'tf__max_features': 2000,
 'tf__ngram_range': (1, 2),
 'tf__stop_words': 'english'}
```
This model gives an accuracy rate of 92.4% for unseen data, outperforming the other models trained in this project (i.e., logistic regression, Multinomial Naive Bayes, DecisionTree, and AdaBoost)

## Conclusions
### Suggestions  
Based on the sentiment analysis and EDA, there is a need for Reddit to include support features, such as a Reddit Bot, to connect Reddit users with resources for mental supports, educational information, and legitimate financial advice.  

### Areas of Improvement
1. Samples - ideally, the more samples, the better.
2. randomization - as there might be some patterns and trends in the Reddit posts/discussion, it might be worth looking at a randomized sample or using bootstrapped methods.  
3. More preprocessing? - there is only minimal preprocessing (e.g., stopwords) is done in this current project. More preprocessing (stemming, lemmatization) could be helpful.
