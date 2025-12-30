## Introduction

Data comes from variety of sources and in different formats. The qualitative and quantitative nature of data also varies. Whereas the quantity of data maybe insignificant, good quality data is vital for making analysis and visualizations for any organizational decision.

This project deals with data wrangling using python libraries. Data wrangling is the process of gathering real data, assessing its quality and tidiness, and then cleaning it. In every step of wrangling, detailed documentations have been made in this project.

The data set for this project is tweet archive of Twitter user @dog_rates (WeRateDogs). According to Udacity, WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. The ratings have Waterdogs constant denominator of 10 but have varying unique numerator. For instance, 12/10, 13/10, etc. WeRateDogs has over 4 million followers. However, this tweet archive data only contains basic tweet data on tweet ID, timestamp, text among others for over 5000 tweets. In addition, more data must be gathered to meet the objective of the project

## Project Motivation

The object of this project is to wrangle WeRateDogs Twitter data to create interesting and trustworthy analyses and visualizations. The Twitter archive only contains very basic tweet information, and additional gathering, then assessing and cleaning is required for a worthy analyses and visualizations.

## What Software Do I Need?

- pandas
- NumPy
- requests
- tweepy
- json
- matplotlib

## Project Steps Overview

1. Gathering data
2. Assessing data
3. Cleaning data
4. Storing data
5. Analyzing, and visualizing data
6. Reporting

## The Data

There are three different types of data for this project, each with different data format.

**a) Enhanced Twitter Archive**

The WeRateDogs Twitter archive contains basic tweet data for all 5000+ of their tweets, but not everything. 

**b) Additional Data via the Twitter API**

The additional data to be gathered and contains retweet count and favorite count, which are the two of the notable column missing from the twitter archive data. The data is queried using tweepy, which ias a Twitter's API to gather this valuable data.

**c) Image Predictions File**

The file contains tweet ID, image URL, and the image number that corresponded to the most confident prediction (numbered 1 to 4 since tweets can have up to four images)

## Gathering Data

There were three different types of data in this project. First, is twitter_archive_enhanced.csv. According to Udacity, WeRateDogs downloaded their Twitter archive and sent it to Udacity via email exclusively for you to use in this project. This data is manually downloaded via the link provided by Udacity and then uploaded in the working directory.

The second data is image_predictions.tsv. This dataset is also known as WeRateDogs tweet image predictions and is hosted on Udacity’s servers. It is downloaded programmatically using requests library [here]('https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv').Using the tweet IDs in the WeRateDogs Twitter archive, I query the Twitter API for each tweet's JSON data using Python's Tweepy library and store each tweet's entire set of JSON data in a file called tweet_json.txt file

Lastly, is tweet_json.txt. There were two methods of getting this additional data. Either, through Twitter API and the python tweepy library or direct download of the json.txt file provided in the Udacity classroom. I queried the data using tweepy API

## Assessing the data

Both visual and progmmatic methods were used to assess quality and tidiness issues.

**Quality issues:** Issues related to the data content (dirty data). We check for four quality dimensions, completeness, validity, accuracy and consistency.

**Tidiness issues:** Issues related to the data structure (messy data). We check whether or not each variable forms a column, each observation forms a row or each type of observational unit forms a table

Through **visual Assessment**, where the data sets were first converted to csv and then opened in an excel workbook, I was able to quickly identify issues as non-descriptive column headers, extraneous columns, missing values (NaN, none), inconsistent rating denominator as well as tidiness issues for dog stage (doggo, floofer, pupper,puppo) in the three Datasets.

In **programmatic Assessment**, I loaded the data sets into pandas data frame in Jupyter notebook and I identified most of the quality issues including incorrect data types, invalid names under name column (a, an, none) and duplicate values existing in the three datasets. The python methods used comprise .info(), .head(), .describe(), .dtypes, .nunique(), .value_counts() and .columns among others. For instance, inaccurate values in twitter_archive data for name column was one of the quality issues identified while the four columns for doggo, floofer, pupper, and puppo were considered dog stage, one variable as a tidiness issue.

## Cleaning the Data

The aim here is to improve quality and tidiness of the data based on the assessment made. In cleaning the data, I used pogrammatic data cleaning process, in which every issue identified in the assessment section is first defined followed by coding and and finally testing. However, copies of the original dataset were made before the issues were cleaned. The three data sets had a lot of unique issues, and at times I had to split the data and clean a particular quality issue and then merge them again. Writing a regex pattern helped in indentifying the correct dog_name and dog_stage.

## Storing the Data

After cleaning the data, the merged data was stored as twitter_archive_master.csv file into the working directory

## Analyzing the Data

Using twitter_archive_master.csv file, three insights were analyzed and visualizations made for each case. One of the insights is that Golden Retriever is the most popular dog breed amongst WeRateDogs’s tweets in terms of the number of image predictions having 139 dogs.

## Insights

1. Pupper dog stage is the most popular dog stage amongst WeRateDogs’s tweets, favorite and retweets counts. The second, most popular dog stage based on the retweets and favorite counts is doggo.

2. There is strong linear relationship between the Favourites count and the Retweet, though most of the data is accumulated at the start. This relationship is the same in every dog stage. Also, the distribution for p1, p2 and p3 is really skewed

3. Golden Retriever is the most popular dog breed amongst WeRateDogs’s tweets in terms of the number of image predictions having 139 dogs. The second most popular dog breed is Labrador Retriever also having 95 dogs. Therefore, golden retriever, labrador retriever, pembroke, Chihuahua and pug make top 5 most popular dog breeds

![image](https://user-images.githubusercontent.com/7541585/193414221-2288a8ea-1699-450c-9eef-2f4cc3a1f938.png)
![image](https://user-images.githubusercontent.com/7541585/193414407-75f2fdbc-5b6a-4663-ab90-a486fa71295d.png)
![image](https://user-images.githubusercontent.com/7541585/193414417-47008729-250a-47a8-a64a-b5cbd9fe52f5.png)
![image](https://user-images.githubusercontent.com/7541585/193414443-47c61010-8556-4312-97c4-187f32455b88.png)
![image](image.png)
![dis_image](python.jpg)

## Limitations

The project identified only three insights. First, the most popular dog stage in terms of retweets and favorite counts. The most popular dog breed as well as their distributions.

It would be of interest to consider the correlation between the tweets and the ratings, which would involve further transformation of data. Another limitation is that, the data had a lot of missing values but I only consider situations where there is valid image url

During cleaning process, there were several invalid dog names, and even after creating regex pattern to extract the correct dog names, there is likelihood that some names still remain unextracted from the text column. This still require further investigation so as extract and correct all the names

## Conclusion

This project was majorly dealing with data wrangling process. There were three different types of data from different sources and formats. First, we have WeRateDogs twitter archive data in a csv format, second is Tweet image prediction in .tsv format and the last dataset is WeRateDogs twitter account additional data tweet to be stored as tweet_json.txt file

All the wrangling efforts are documented at every section.

The major findings of this analysis are that Pupper dog stage is the most popular dog stage amongst WeRateDogs’s tweets, favorite and retweets counts. The second, most popular dog stage based on the retweets and favorite counts is doggo. Whereas I was able to show that there is a correlation between the Favourites count and the Retweet, I have to indicate that most of the data accumulated at the start of the graph, which might skewness.

lastly, Golden Retriever is the most popular dog breed amongst WeRateDogs’s tweets in terms of the number of image predictions having 139 dogs. Others making top five include labrador retriever, pembroke, Chihuahua and pug.
