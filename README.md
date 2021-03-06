
## Installation de java & maven 

```sh
yum install java 
yum install wget
wget http://mirrors.standaloneinstaller.com/apache/maven/maven-3/3.5.4/source/apache-maven-3.5.4-src.tar.gz
tar xfvz apache-maven-3.5.4-src.tar.gz
wget http://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo
yum -y install apache-maven
mvn -f apache-maven-3.5.4/pom.xml
```
## Installation de YCSB 
```sh
curl -O --location https://github.com/brianfrankcooper/YCSB/releases/download/0.14.0/ycsb-0.14.0.tar.gz
tar xfvz ycsb-0.14.0.tar.gz
cd ycsb-0.14.0
```
## Run YCSB

Run YCSB command

Pour Linux: 
```sh
./bin/ycsb.sh load basic -P workloads/workloada
./bin/ycsb.sh run basic -P workloads/workloada
```
Pour Windows:
```bat
./bin/ycsb.bat load basic -P workloads\workloada
./bin/ycsb.bat run basic -P workloads\workloada
```
Building from source
--------------------

YCSB requires the use of Maven 3; if you use Maven 2, you may see [errors
such as these](https://github.com/brianfrankcooper/YCSB/issues/406).

To build the full distribution, with all database bindings:

    mvn clean package

To build a single database binding:

mvn -pl com.yahoo.ycsb:mongodb-binding -am clean package

## Installation de Hbase 
```
wget http://archive.apache.org/dist/hbase/hbase-2.0.0-beta-1/hbase-2.0.0-beta-1-bin.tar.gz 
tar xfvz hbase-2.0.0-beta-1-bin.tar.gz
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.181-3.b13.el6_10.x86_64/jre
./start-hbase.sh
./hbase shell
```

## Creation d'une table dans Hbase 
```sh
./hbase shell
create 'usertable', 'family'
```
## Installation de Hadoop
```sh
wget http://apache.mindstudios.com/hadoop/common/hadoop-2.7.7/hadoop-2.7.7.tar.gz
tar xfvz hadoop-2.7.7.tar.gz
cd hadoop-2.7.7/bin
./hadoop verison 
```
## Teste de performance de Hbase 

```sh
./ycsb load hbase10 -P workloads/workloada -p columnfamily=f1 -p recordcount=1000000 -threads 10 -s > new-A-load-1M.dat
./bin/ycsb.sh load hbase10 -P workloads/workloada -p columnfamily=f1 -p recordcount=1000000 -threads 10 -s > new-A-load-1M.dat
./bin/ycsb.sh run hbase10 -P workloads/workloada -p columnfamily=f1 -p recordcount=1000000 -threads 10 -s > new-A-load-1M.dat
./bin/ycsb.sh load hbase10 -P workloads/workloada -p columnfamily=family
./bin/ycsb.sh run hbase10 -P workloads/workloada -p columnfamily=family
```
