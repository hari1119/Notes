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
  - ```tar -xvf filename.tar``` use this command to Extract the .tar file.
  - Open as terminal and open a ```.bashrc``` file
  - Move the courser to the end and add the env for the java and hadoop
  - ```
    export JAVA_HOME=/home/hari/jdk1.8.0_202
    export HADOOP_HOME=/home/hari/hadoop-2.9.2

    export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$PATH
    ```
  - Run the ```.bashrc``` file using the ```source .bashrc``` command
  - After running the above command, Check the Java version using ```java -version```

# Modify Hadoop Configuration Files
  - NAMENODE ----> core-site.xml
  - RESOURCE MANGER ----> mapperd-site.xml
  - SECONDARYNAMENODE ---->
  - DATANODE ----> slaves
  - NODEMANGER ----> slaves & yarn-site.xml



### *Notes :* Add the below code in between the ```<configuration>``` tag or Copy the `etc/hadoop/core-site.xml.template` and rename.
**File:** `etc/hadoop/core-site.xml`
```xml
<property>
<name>fs.default.name</name>
<value>hdfs://localhost:50000</value>
</property>
```

**File:** `etc/hadoop/yarn-site.xml`
```xml
<property>
<name>yarn.nodemanager.aux-services</name> <value>mapreduce_shuffle</value>
</property>
<property>
<name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name> <value>org.apache.hadoop.mapred.ShuffleHandler</value>
</property>
<property>
<description>The hostname of the RM.</description>
<name>yarn.resourcemanager.hostname</name>
<value>localhost</value>
</property>
<property>
<description>The address of the applications manager interface in the RM.</description>
<name>yarn.resourcemanager.address</name>
<value>{yarn.resourcemanager.hostname}:8032</value>
</property>
```
**File:** `etc/hadoop/hdfs-site.xml`
```xml
<property>
<name>dfs.namenode.name.dir</name>
<value>/home/username/hadoop2-dir/namenode-dir</value>
</property>
<property>
<name>dfs.datanode.data.dir</name>
<value>/home/username/hadoop2-dir/datanode-dir</value>
</property>
```

   - ```mapred-site.xml``` want to create the file manually.
**File:** `etc/hadoop/mapred-site.xml`
```xml
<property>
<name>mapreduce.framework.name</name>
<value>yarn</value>
</property>
```

**File:** `etc/hadoop/hadoop-env.sh`
```sh
export JAVA_HOME=/home/username/jdk1.8.0_45
```

**File:** `etc/hadoop/mapred-env.sh`
```sh
export JAVA_HOME=/home/username/jdk1.8.0_ 45
```

**File:** `etc/hadoop/yarn-env.sh`
```sh
export JAVA_HOME=/home/username/jdk1.8.0_45
```
**File:** `etc/hadoop/slaves`
```
localhost
```
# Install SSH-Server
```sh
sudo apt-get install openssh-server
```
# Install the ssh key
(Generates, Manages and Converts Authentication keys)
```sh
 ssh-keygen -t rsa
```
(Setup passwordless ssh to localhost and to slaves )
```sh
 cd .ssh
 ls
 cat id_rsa.pub >> authorized_keys (copy the .pub)
```
(Copy the id_rsa.pub from NameNode to authorized_keys in all machines)
```sh
ssh localhost
```
(Asking No Password )

# Format NameNode
```sh
 cd hadoop-2.9.1
```
```sh
 bin/hadoop namenode -format
```
 (Your Hadoop File System Ready)
 ```log
Storage directory /tmp/hadoop-aspireal/dfs/name has been successfully formatted.
```
- If we seen the above log means everything installed fine.

# Start All Hadoop Related Services

```sh
 sbin/start-all.sh
```
(Starting Daemon’s For DFS & YARN)

- To list all the nodes

```sh
jps
```

```sh
NameNode
DataNode
SecondaryNameNode
ResourceManager
NodeManager
```

(check the Browser Web GUI )
   - [NameNode](http://localhost:50070/) - http://localhost:50070/
   - [Resource Manager](http://localhost:8088/)- http://localhost:8088/

# Stop All Hadoop and Yarn Related Services

```sh
 sbin/stop-all.sh
```
