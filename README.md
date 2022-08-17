# Amazon Vine Analysis
## Overview
Using apache spark, data from AWS Simple Storage Service (S3), was extracted into google colab. The data was then transformed using pyspark, and organized by schema. Using AWS RDS, PGAdmin, postgreSQL, and pyspark, the transformed data was loaded into the database. 

Using the same digital music review data from AWS S3, the vine review data was further transformed and filtered by: reviews with total votes greater than or equal to 20, helpful votes greater than or equal to 50% of the total votes, paid and unpaid review status. Analysis of the paid and unpaid reviews were observed using the total number of reviews, the number of 5-star reviews, and percentage of 5-star reviews to the total for each category. 

### Purpose
The purpose of this project was to compare paid reviews and non-paid reviews using digital music review data, publicly available in AWS S3, and observe any biases.

### Resources
**Data retrieval:** [Amazon Music Reviews](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Digital_Music_Purchase_v1_00.tsv.gz)<br>
**Tools:** Google Research Colab, AWS RDS, AWS S3, PGAdmin, Apache Spark, Pyspark, Python, PostgreSQL <br>
**Outputs:** 
 - Code Files: [Review Tables Schema](/Code/reviews_schema.sql), [Reviews ETL Notebook](/Code/Amazon_Reviews_ETL.ipynb), [Vine Analysis Notebook](/Code/Vine_Review_Analysis.ipynb)
 - Data Files: [Aggregated Customer Count](/Data%20Tables/customers.csv), [Products List](/Data%20Tables/products.csv), [Review Indexed by Customer and Product](/Data%20Tables/reviews.csv), [Review Rating and Vine Data](/Data%20Tables/vines.csv)

## Results
<br>**Image 1. Filtered Paid Reviews**
<br>![Image link](/Images/paid_reviews.png)
<br>Image 1. Shows the dataframe created from the filtered data of paid reviews.
<br>
<br>**Image 2. Filtered Unpaid Reviews**
<br>![Image link](/Images/unpaid_reviews.png)
<br>Image 2. Shows the dataframe created from the filtered data of unpaid reviews.
<br>
<br>How many Vine reviews and non-Vine reviews were there?
 - As seen in Image 1, there were 0 Vine reviews. 
 - Non-vine reviews totaled 4,533.<br>
How many reviews were 5 stars?
 - Of the non-vine reviews, 2,507 of wich were 5-star ratings.<br>
What percentage of reviews were 5 stars?
 - This yielded a 55.3% of total non-vine reviews being 5-star rating. 

## Summary
Unfortunately, there was not enough data to determine the bias of the paid vs non-paid reviews. Once the data had been filtered, there were 0 instances of paid reviews that matched the criteria. Some possible explanations below:
 1. Paid reviews are more common in instances of low total votes (less than 20).
 2. Paid reviews are more obvious to the reader/customer, and do not receive "helpful" rating as often as non-paid reviews. 
 
Additional anylses to substantiate bias claims, could be to measure the variance between paid reviews and non-paid reviews without filtering data. This would show whether there is a measureable difference between paid review and unpaid review per product.