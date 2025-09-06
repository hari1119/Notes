# Hive Instalations.
  - Make sure before installing hadoop install and running in your machine, ```jps``` use this commands to check the hive is running or not.

  # Download Apache Hive
  - [Download Link](https://apache.root.lu/hive/hive-3.1.2/) make use the download file should be end with ```*-bin.tar.gz```
  - Move to the home folder and ```tar -xvf filename.tar``` use this command to Extract the .tar file
  - install the mysql or postgres db in you system, command to install mysql ```sudo apt-get install mysql```
  - Download the connecter .jar file from the mvn
  - [mysql connector](https://mvnrepository.com/artifact/com.mysql/mysql-connector-j/9.3.0) once downloaded and move to the ```hive/lib/```
  - Go to the conf file and create a file ```hive-site.xml``` replace the contect for the mysql connectivity.
    ``` xml
          <?xml version="1.0" encoding="UTF-8" standalone="no"?>
          <?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
          <configuration>
            <property>
              <name>javax.jdo.option.ConnectionURL</name>
              <value>jdbc:mysql://localhost/metastore?createDatabaseIfNotExist=true</value>
            </property>
            <property>
              <name>javax.jdo.option.ConnectionDriverName</name>
              <value>com.mysql.jdbc.Driver</value>
            </property>
            
            <property>
              <name>javax.jdo.option.ConnectionUserName</name>
              <value>root</value>
            </property>
            
            <property>
              <name>javax.jdo.option.ConnectionPassword</name>
              <value>root</value>
            </property>
            <property>
            <name>hive.metastore.schema.verification</name>
            <value>false</value>
            </property>
          </configuration>
    ```
  - [postgres connector](https://mvnrepository.com/artifact/org.postgresql/postgresql/42.7.6) once downloaded and move to the ```hive/lib/```
  - Go to the conf file and create a file ```hive-site.xml``` replace the contect for the postgres connectivity.
    ``` xml
          <?xml version="1.0" encoding="UTF-8" standalone="no"?>
          <?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
          <configuration>
            <property>
              <name>javax.jdo.option.ConnectionURL</name>
              <value>jdbc:postgresql://localhost:5432/metastore</value>
            </property>
            
            <property>
              <name>javax.jdo.option.ConnectionDriverName</name>
              <value>org.postgresql.Driver</value>
            </property>
            
            <property>
              <name>javax.jdo.option.ConnectionUserName</name>
              <value>odoo</value>
            </property>
            
            <property>
              <name>javax.jdo.option.ConnectionPassword</name>
              <value>odoo</value>
            </property>
            <property>
            <name>hive.metastore.schema.verification</name>
            <value>false</value>
            </property>
          </configuration>
    ```
    - create a databse as ```metastore```
    - After the db created go to the hive folder and type ```bin/schematool -dbType postgres -initSchema``` run this cmd to create a hive schema, in-case of mysql replace the postgres and try with mysql
