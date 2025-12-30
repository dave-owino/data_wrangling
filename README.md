# Multi-Source ETL Pipeline: Twitter Data Ingestion & Transformation

1. Project Overview

This project demonstrates a robust Data Engineering pipeline designed to ingest, transform, and store fragmented data from three distinct sources: live API streams, cloud-hosted files, and archival datasets. The core objective was to wrangle the Twitter account data of @dog_rates (WeRateDogs) to create a high-integrity "Gold" dataset for trustworthy analysis and visualization.

2. Technical Stack & Software Requirements

- Language: Python

- Data Ingestion: Tweepy (REST API), Requests (Cloud HTTP Ingestion)

- Transformation: Pandas, NumPy, Regular Expressions (RegEx), JSON

- Visualization: Matplotlib, Seaborn

3. Data Pipeline Architecture (ETL)

The pipeline manages three unique data streams, each requiring a different ingestion strategy:

- Stream A (Archival - Extract): Manual ingestion of the twitter_archive_enhanced.csv provided by Udacity, containing basic metadata for 5,000+ tweets.

- Stream B (Cloud - Ingest): Programmatic ingestion of the image-predictions.tsv file hosted on Udacity’s servers via the Requests library.

- Stream C (Live API - Query): Dynamic extraction of missing data (retweet/favorite counts) using Tweepy to query the Twitter API. Raw responses were serialized into a tweet_json.txt file before parsing.

4. Data Quality & Wrangling Framework

Following the MSc Data Engineering standard, this project follows a strict "Assess-Clean-Test" workflow. Detailed documentation was maintained at every step to ensure transparency.

## Assessment Dimensions

Both Visual (Excel-based) and Programmatic (Pandas-based) assessments were conducted to identify issues across:

- Quality: Completeness, Validity, Accuracy, and Consistency (e.g., incorrect data types, invalid names).

- Tidiness: Structural issues where variables did not form clear columns (e.g., dog stages spread across four columns).

Key Engineering Challenges Resolved:

- API Rate Limiting: Built a robust wrapper to handle the query of thousands of unique Tweet IDs via the Twitter API.

- JSON Normalization: Flattened nested JSON structures into a relational tabular format.

- Advanced Pattern Matching: Developed RegEx patterns to extract correct dog_name and dog_stage information from unstructured tweet text.

- Schema Denormalization: Merged three disparate data formats into a single, high-integrity twitter_archive_master.csv.

5. System Insights & Findings

- Infrastructure Efficiency: Successfully synchronized metadata across the dataset after filtering for valid image URLs and removing retweets.

- Core Trends: Identified "Golden Retriever" as the most frequent breed (139 dogs), followed by "Labrador Retriever" (95 dogs).

- Dog Stages: "Pupper" emerged as the most popular stage by count, while "Doggo" ranked second based on retweet and favorite metrics.

- Statistical Correlation: Observed a strong linear relationship between Favorite counts and Retweet counts across all stages.

6. Limitations & Future Scope

- Extraction Accuracy: Despite RegEx implementation, some edge-case naming conventions in the text column may remain unextracted.

- Data Completeness: The analysis was limited to tweets with valid image URLs; further transformation could include rating-to-tweet correlations.

- Pipeline Scalability: Future iterations will migrate this local ETL workflow into a cloud-native environment (e.g., Airflow or AWS Lambda) for scheduled ingestion.


This project was completed as part of the Udacity Data Analyst Nanodegree, focusing on the end-to-end data wrangling process.
