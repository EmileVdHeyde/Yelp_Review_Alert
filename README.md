# Yelp_Review_Alert
Data Engineering Project 

Purpose:

Build a Real-time spam alert system for Yelp reviews to report users posting a high volume of comments in a defined period of time (Alert 1), businesses getting high volume comments in specified period of time (Alert 2). In Addition, a Machine Learning language model which in near real time moderates and alerts abusive language (Alert 3) in a reviews free text. 



![Final Design](https://user-images.githubusercontent.com/8738489/127738869-4ffc72d4-44bf-4166-947a-7f513d989a99.png)




# Set up 

1.	Data source
      Download data from https://www.kaggle.com/yelp-dataset/yelp-dataset
      See python code to create a sample of the data in the DATA folder. 


2.	Set up docker containers 

      This script creates 4 containers; 1 kafka, 2 spark containers , 1 Zoo Keeper , Using the yml file provided. Remember to change to your IP address. 
      Additionally run the python packages script, which install all the needed python packages.

      Command: docker-compose up -d 


3.	Distributed Database- Cassandra set up 
      I had created a folder called Cassandra_data to store all folders related to cassandra database. Create the following docker container and start cassandra.  
      
      Command: docker run -P -p 9742:9042 -v /root/de/cassandra_data:/var/lib/cassandra -d --name=cassandra Cassandra

      You can connect this database to a client front end. For example I used TablePlus. I built the table spaces and table definitions within this client tool. 

4.	Run Spark (Container 3) 
      
      Command: docker exec -it docker_spark_1 bash jupyter notebook list

      This will open the Jupiter notebooks in local internet browser. I had created a folder for Data , and within two folders; detail (For Parquet files) and cp         (Check Points) within it.The notebooks contain Producer 1 which can be run to start the stream of data. A second note book plays the role of consumer. It has       3 parts ; Parque files, Aggregation and time windowed alerts. To visualise the summaries data a notebook called visualisation is provided.  There is an             additional script to ad hoc push the parquet files to the Cassandra database. 

5.	Run Spark (Container 4) 

      docker exec -it docker_spark1_1 bash jupyter notebook list
      This will open the Jupiter notebooks1 in local internet browser. I had created a folder for Data , and within two folders; detail (For Parquet files) and cp         (Check Points) within it. Also included is all model artifacts such as a pickle file of the NLP model, as well as tokenizer files. The notebooks contain             Producer ML which starts the text stream, And consumer 2 and 3.



# Results 








