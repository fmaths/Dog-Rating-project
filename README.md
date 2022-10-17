# Dog Rating project
## by Fidelis Mukudi


## Introduction

The project was about the analysis of data in a Twitter account by the user name @dog_rate also called WeRateDogs. On the account, Twitter user rate dogs and provide comments on them. The rating has a denominator of 10 with a denominator of a number more than 10. 

In this project, we were provided with two data sets, twitter_archive_enhanced.csv and image predictions.tsv data. The first data contained tweet details except for the favorite counts and the retweet counts. This data was extracted manually. The second data contained the details of dog images. A link was provided, hence, the data was programmatically extracted. Since the data from twitter_archive had retweets as well, we used the tweet_ids from the image-prediction data to filter our
data having original tweets only. This was based on an assumption that the image is only attached to the original tweets.

The information contained in the two data sets was not enough to make informed insights on dog ratings, as such, we gathered a third data set from the Twitter account using the Twitter API. The data was cleaned and the following questions were answered; 
* Which dogs have the highest and the lowest average rating?
* What is the dog ranking based on the average favorite counts and the average number of retweets?
* Do the dogs with higher have higher favorite counts and number of retweets
* What is the effective percentage ranking of the dogs based on the favorite counts, number of retweets, and ratings? Does the ranking based on the effective percentage agree with the other rankings used earlier? 

## Data Wrangling report
### Gather data
The project is about rating the dogs using data from the Twitter account WeRateDogs. Two data were provided where *twitter_archive_enhanced* and *image predictions*. The first one was manually extracted and while the second one was programmatically extracted. I gathered them as required. For the third data set, I used gathered the data from Twitter using the Twitter API. I used the key and tokens provided by the Twitter development account to query the API created a file and read the tweet one by one as I dumped them into a JSON file and wrote them line by line into a text file. Using the text file, I loaded each line to JSON and then created a list of dictionaries that helped me create a data frame called additional_tweet_data.

### Assess
Next, I moved to assess the data. I used both visual and programmatic assessments on the three data and wrote a number of quality and tidiness issues that I wanted to address. The issues were related to the research questions that I wanted to answer at the end of the cleaning process. the issues were as shown below

#### Quality Issues
###### twitter_archive_data
* Drop rows representing retweets
* Drop rows representing replys to users
* Drop columns that we will not use in our analysis
* Extract years from the timestamp columns
* Rename the numerator, timestamp
* Drop rows where the numerator is less than 10
* Drop rows having null and none entries
* Drop duplicated entries
* Clean the dogs name column to ensure that no row has two or more dog names

###### image_predict_data and twitter_archive_data
* Drop rows that do not have corresponding image in the time-prediction data


#### Tideness Issues
* Collapse the doggo,floofer,pupper and	puppo columns into one column
* Combine the tables into one table to form one observational unit 


### Clean data
I moved to clean the data. I cleaned the *twitter_archive_enhanced* copy based on the list of issues outlined above. First, I removed rows having retweets and replies to ensure that I have original tweets. Second, I removed the rows that were not required to carry out the analysis. Then I extracted the years from the timestamp so that I can check if there is any row whose year comes after 2017. Next, I renamed the ratings and the timestamp column then dropped a number of rows that had less than 10 numerator ratings. I filtered the rows to ensure that the ids in my dataset have corresponding images from the image prediction file. 
Thereafter, I moved to the tidiness issue, where I melted a number of rows into a dog name row and proceeded to delete rows with null entries. I then checked for rows with more than two dog names but there weren’t any. Next, I moved ahead to ensure that the twitter_archive_enhanced data have the same Twitter ids with additional_more_Twitter data after which I merged them. In the process, I dropped duplicate rows. Finally, I stored the final clean data frame as a CSV file.




## Summary of Findings

In the project, found that Puppo is the most highly ranked dog name followed by popper and doggo is the least ranked one. We were not able to get a better rank for floofer because we had limited data to understand help us rank it. It only have one value. 

We also found that the dog names with higher ranking had more average favorite counts and retweet counts compared to others. On the other hand, the dog name with the lowest ranking had fewer average favorite counts and retweet counts compared to others.

Finally, we came up with a metric that combined the ranking, the favorite count and the retweet counts. The new metric gave us results that were in agreement with the rankings of the dogs as done with the earlier metrics.



## Limitations
The main limitation is that the scope of the data was limited to 2017 or later and most rows had no dog ratings. As such, we had very few data rows at the end of the cleaning. For instance, the floofer dog had one rating only in the final data. This does did not give us a sufficient result that can be replicated when the same report is done on a bigger data set.
