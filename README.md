# Classification of News Article Subreddit Posts
### By Jamie McElhiney

I am a member of a news agency that promotes our content on reddit. We want to post a breaking news story ASAP on the correct news subreddit so we can get exposure and traffic on our website since all posts on the subreddit are third party links. There are 2 main news subreddits r/worldnews and r/news that are very similar. There is no clear cut topic that separates these two subreddits. We don’t want to post the article on both subreddits and hope for the best since we can be marked for spam, leading to our article being deleted and a warning from reddit. We also want to uphold our reddit reputation as people call each other out for crossposting often.   
We are going to use these two subreddits, r/worldnews and r/news, to develop a classification model that will recommend which subreddit to post our breaking story to based on our title. We will develop three different classification models to classify our news article: LogisticRegression, Naive Bayes, and K-Nearest Neighbor. 

## Executive Summary

We are going to be using the subreddit data scraped by our data retrieval notebook which can be found [here](../project_3/p3_DataRetrieval.ipynb). The output csv can also be directly referenced [here](../project_3/datasets/subredditdata.csv). The dataframe is concatenated from two separate scraping queries targeting our two subreddits, r/news and r/worldnews. We are going to be developing a classification model based on the title of the subreddit post so we can determine which subreddit is most appropriate for our drafted news article. We used a regular expression tokenizer to remove unwanted characters from subreddit post titles. A stemmer was implemented after cleaning titles to find common root words and more efficiently recognize patterns within our corpus.  
So, If we are able to post the article to the more relevant subreddit, our post will receive more exposure leading to more traffic on our website and thus revenue from ads. Given the similar nature of the two subreddits, our task at hand is challenging and we did not receive many low bias models. The evaluation metric we will use in this case is accuracy, the number of correct predictions over the number of total predictions. We were able to develop a Multinomial Naive Bayes model with 65% accuracy. 

## Data Dictionary 

|Feature|Type|Dataset|Description|
|---|---|---|---|
|title|object|news|title of subreddit post|
|subreddit|object|news|name of subreddit|
|created_utc|int64|news|unix timestamp|
|author|object|news|reddit username of poster|
|num_comments|int64|news|number of comments|
|score|int64|news|difference between upvotes and downvotes|
|url|object|news|link to 3rd party site in post|
|timestamp|datetime64|news|date of post|

## Conclusion and Recommendations

After evaluating our models, we came to the conclusion that our Multinomial Naive Bayes had relatively low bias and low variance. It also had an accuracy score of 0.65 which, in the context of the problem, is not half bad. To reiterate, these subreddits are super similar. I wanted to attempt this problem statement to see if there was something I was missing all this time as to why there are two major news subreddits that seemingly post the same content. I cannot confidently say that this is a strong classifier in the context of the problem. I would recommend using it as an initial guess as to where to post an article but to also use some basic intuition when delpoying this specific model.    
Some additional features I could add would be to access the article text by creating a soup object from the html, and appending the body text to the subreddit dataframe. Then from there vectorize and run classification.  