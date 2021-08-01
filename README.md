# Yelp_Review_Alert
Data Engineering Project 

Purpose:

Build a Real-time spam alert system for Yelp reviews to report users posting a high volume of comments in a defined period of time (Alert 1), businesses getting high volume comments in specified period of time (Alert 2). In Addition, a Machine Learning language model which in near real time moderates and alerts abusive language (Alert 3) in a reviews free text. 



![Final Design](https://user-images.githubusercontent.com/8738489/127738869-4ffc72d4-44bf-4166-947a-7f513d989a99.png)




Set up 

1. Set up docker containers (This scriot creates 4 containers; 1 kafka, 2 spark containers , 1 Zoo Keeper)
docker-compose up -d
Remember to change to your IP adress
Additionall run the python packages script which install all the needed python packages. 

2.Add a folder to add the Cassandra data base file, and create its container 
docker run -P -p 9742:9042 -v /root/de/cassandra_data:/var/lib/cassandra -d --name=cassandra cassandra

3.Run Spark (Container 3)
docker exec -it docker_spark_1 bash
jupyter notebook list

http://xxx.xxx.xxx.xxx:8888/

Create a folder for Data , and two folders detail (For Parquet files) and cp (Check Points) within it  


4.Run Spark (Container 4)
docker exec -it docker_spark1_1 bash
jupyter notebook list

http://xxx.xxx.xxx.xxx:8889/

Create a folder for Data , and two folders detail (For Parquet files) and cp (Check Points) within it  

5. Data source 

Download data from https://www.kaggle.com/yelp-dataset/yelp-dataset 
See python code to create a sample of data to stream in the Data Folder. 







