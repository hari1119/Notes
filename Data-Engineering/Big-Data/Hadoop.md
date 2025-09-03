# Hadoop Framework
  - HDFS -> Hadoop Distributed File Sharing
  - MR -> Map Reduse


## Hive
 - innovated by the facebook to communicate with the MR use the SQL instead of JAVA, it's convert the SQL to JAVA for the communication with the MR

## Sqoop
 - Sqoop is use to make a connection between the RDBMS and the MR, data fetching and the data loading both will be handle by the sqoop.

## Oozie
 - A workflow scheduler for managing Hadoop jobs.

## hbase
 - NOSQL database used in the hadoop framework

## Mahout
 - we can do the data science related stuffes and the ML & AI in the mahout

## Flume
 - Stream the data retrieving from the multiple resouces, only fetch not loading like a Sqoop

# Hadoop Instalations

  - Make sure the ubuntu OS is installed
  - ``` uname -a ``` to find the system bites, like 64 or 32
  - [Hadoop Download](https://archive.apache.org/dist/hadoop/common/hadoop-2.9.2/) Click the link to download the hadoop, make sure it should be a ur system matching bits like 64bits, download the file ends with *.tar.gz composed one.  
  - [Java Download](https://www.oracle.com/in/java/technologies/javase/javase8-archive-downloads.html) Click the link to download java, make sure it should be a your system matching bits
  - After Downloaded more the files to the Home to start.
  - Open as terminal and open a ```.bashrc``` file
  - Move the courser to the end and add the env for the java and hadoop
  - ```
    export JAVA_HOME=/home/hari/jdk1.8.0_202
    export HADOOP_HOME=/home/hari/

    export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$PATH
    ```
  - Run the ```.bashrc``` file using the ```source .bashrc``` command
  - After running the above command, Check the Java version using ```java -version```
  - 


