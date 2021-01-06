## kafka-nodejs

### Install Kafka on remote Ubuntu Server
### Sign up into the https://cloud.digitalocean.com/ and pick up a droplet ubuntu basic
### Sign in into the server via console
```
    ssh root@206.81.26.251
```
### Type for updating software
```
    sudo apt-get update
``` 
### Installing jdk-11
```
    sudo apt install openjdk-11-jdk
```
### Check Java version
```
    java --version
```
### Create folder downloads into Ubuntu Server
```
    mkdir Downloads
```
### Choose a binary downloads link from https://kafka.apache.org/downloads Scala 2.12  - kafka_2.12-2.7.0.tgz (asc, sha512)
```
    curl https://apache.volia.net/kafka/2.7.0/kafka_2.12-2.7.0.tgz -o Downloads/kafka.tgz
```
### Create kafka folder
```
    mkdir kafka
    cd kafka
```
### Type into server
```
    tar -xvzf ~/Downloads/kafka.tgz --strip 1
```
### In /config folder we have server.properties configuration file and in /bin folder we have a scripts
### Starting Zookeeper
```
    bin/zookeeper-server-start.sh config/zookeeper.properties
```
### Start Kafka broker
```
    bin/kafka-server-start.sh config/server.properties
```
### Got to logs on server
```
    cd /tmp/kafka-logs/
```
### Create first kafka topic
```
    bin/kafka-topics.sh
    bin/kafka-topics.sh --create
```
### Create topic (ubuntu-kafka)
```
    bin/kafka-topics.sh --create --bootstrap-server localhost:9092
    bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --topic cities
```
### Got to logs dir
```
    cd /tmp/kafka-logs/cities-0
```
### In file server.properties we can see string "num.partitions=1", It's a number of partitions creating by default

### List of Kafka topics
```
    bin/kafka-topics.sh sh --list --zookeeper localhost:2181
```
### Configutation details for topic
```
    bin/kafka-topics.sh sh --describe --zookeeper localhost:2181 --topic cities
```
### Send Message
```
    bin/kafka-console-producer.sh --topic cities --bootstrap-server localhost:9092
    or
    bin/kafka-console-producer.sh --broker-list localhost:9092 --topic cities
```
### Receiving message
```
    bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic cities
```
### For reading all the messages type
```
    bin/kafka-console-consumer.sh --topic cities --from-beginning --bootstrap-server localhost:9092
```


























