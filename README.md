1-Setting up the Environment:

Bash:

1-
I have uploaded crimedata.csv to Github to get it public and wget the raw file , so I can get the data and work on it.
For bash, I had to load the docker we start with our first container, I have opened the docker to see how many files I have there before doing anything else, the first command I used was this:
$ docker run -tid --name aNameYouLike registry.gitlab.com/roddhjav/ucd-bigdata/bash
I can change the name anyway I like for example I can remove the ANameYoulike and replace it with any name I want.
2- In the second part I used docker, and tell the docker to run ubuntu, this is the second Apr I used:
$ docker ps
3- for the third part I had to start the container to get it running
$ docker start aNameYouLike
4- for the fourth part I had to execute it which will open the bash command line in the container where you can do the rest of the bash scripts.
docker exec -it aNameYouLike bash
to open a file I had to use nano and call it any name for a specific file question for example nano “Q1.sh”, to execute it I need to do this: $ chmod u+x Q1.sh 

then $ ./Q1.sh to run the file on the command prompt.


2- Setting up my environment database management  
MYSQl:

- I have uploaded Players.csv and teams.csv  to Github to get it public and wget the raw file , so I can get the data and work on it.
-  to run the create SQL table go to mysql when loaded in bash and the write “source create. SQl” to run,  
- for populating the SQL go back to the bash create a nano file, then run it with the same steps that I did in the first part for the bash command,
 - to run the basic SQL queries just simply got to mysql by typing it in bash then right the source and the file for example “source Q1.sql”, and make sure its capital Q when running the files for the SQL queries.
Mongo:

- for populating the mongo  go back to the bash create a nano file, then run it with the same steps that I did in the first part for the bash command , note because this is mongo , there’s no need to  go mongo and create database , just simply run it in the bash file with same commands as usually we do for the bash files , it will automatically create the database for you no need to go mongo.
- to perform the queries, you can use .js files and the command will help you run the queries in bash and not mongo! Is as an example: mongo sportDB Q5.js, so it can run, it will only show the answer at the start so don’t look at the rest of the code.


3-Setting up the Environment:

Hadoop

To get Hadoop working for windows I have went to windows PowerShell to get Hadoop running the first I have done was “CD docker-hadoop”.
-I used $ docker ps because this following command will show the list of containers running.
- I used $ docker exec -it namenode bash this will run a Hadoop MapReduce job and connect to the name node.
-  I have used wget to get the file into the machine 
- after that I followed the lab 5 by doing $ hdfs dfs -mkdir /dataset1
- after that $ hdfs dfs -mkdir /input
 I copied from the local $ hdfs dfs -copyFromLocal ./input/* /input
Then to check the local if the files have been uploaded:
$ hdfs dfs -ls /dataset1
$ hdfs dfs -ls /input
After doing all this steps now we can execute the MapReduce by using
Wget --no-check-certificate csserver.ucd.ie/~aventresque/hadoop-mapreduce-examples-2.7.1-sources.jar
To execute the Hadoop job wordcount I use this command:
hadoop jar hadoop-mapreduce-examples-2.7.1-sources.jar org.apache.hadoop.examples.WordCount /input /output
now we download the wordcount java that will do all the work for us , for all the java questions: wget --no-check-certificate csserver.ucd.ie/~aventresque/COMP30770/2020/WordCount.java
I copied many times the wordcount for the rest question by using this command:
cp WordCount.java WordCount2.java and kept doing that until it reached wordCount5.
To edit the file simply use: nano WordCount2.java
To compile the file, I used this: export HADOOP_CLASSPATH=/usr/lib/jvm/java-1.8.0-openjdk-amd64/lib/tools.jar 
hadoop com.sun.tools.javac.Main WordCount2.java
to create a jar file: jar cf wc.jar WordCount2*.class
and finally to execute a file: hadoop jar wc.jar WordCount2 /input /output2

some of the files when I was running them they were called Wordcount, Wordcount2, Wordcount3, Wordcount4, Wordcount5 , but I changed them when I submitted. To Part3_Q1.java etc…

4- setting up the environment:
Spark
To get the spark, I have used the following commands to run the code

First step was loading the docker to run:
docker run --name spark-master -h spark-master -e ENABLE_INIT_DAEMON=false -d bde2020/spark-master:3.0.0-hadoop3.2-java11
to start the spark:
docker run --name spark-worker-1 --link spark-master:spark-master -e ENABLE_INIT_DAEMON=false -d bde2020/spark-worker:3.0.0-hadoop3.2-java11
to execute it :
docker exec -it spark-master bash
and to get spark working and launching: 
/spark/bin/spark-shell
