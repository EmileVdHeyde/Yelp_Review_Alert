# Yelp_Review_Alert
Data Engineering Project 

Conception
Purpose: Build a Real time spam alert system for Yelp reviews to report users posting high volume of comments in defined period of time (Alert 1), business getting high volume comments in defined period of time (Alert 2). In Addition a Machine Learning language model which in near real time moderates and alerts abusive language (Alert 3) in a reviews free text.

Process: (1) Simulate a stream of data with python using Json file. (2) Produced into Kafka. (3) Consumed with the Spark , and perform continuous time window aggregations. (4) Alert if thresholds breached (5) Store history in MySQL database for reporting. (6) ML model will take in text and score with Language model. When high probability of offensive , alert 3 is sent immediately. (7) All incoming raw data is stored in a data lake stored in Parquet files.

Architecture Choice: Spark and Kafka are high tech scalable tools for real time processing. MySql database is best for reporting trends and user analysis. Data lake optimised storage with all information streaming for safe keeping and further aggregations if needed. Kappa Architecture allowing a singular near real time system. Downside is that ML calculation may slow the process.

##Implementation

Two independent streams design
Fast streaming for alerting number of users and business posts.
Slightly slower and more data intensive ML text prediction stream. Each stream acts as a microservice that serves different purposes and writes to its own database. If one fails the other can still continue. This is manifested in two separate producers and two spark containers for each stream.
Parque file writes For back up purposes , we write to parquet files in both streams. These files store ALL data incoming and outputs. Parque columnar storage consumes less space and will not be queried for real time purpose.

Distributed Database Cassandra Casandra offers fast read and continuous availability as well as a distributed database allowing for data replication enhancing reliability. It offers an easily accessible eventually unified view of both streams for business.

Aggregation and window functions for real time I used fixed time intervals of 1 minute to aggregate streams to push for the dashboard information. Time window function to count between the time period between users posts alerts.

Application of streaming data & ML model Python Model predictions produced and streamed as new kafka topic feed into spark.

#Instructions

Final Design

1 Creating the Files

Creating the Containers
2.1 Kafka, Spark and Zookeper

2.2 Casandra

Folder Systems set up

Outupt for STREAM 1

Outupt for STREAM 2
