<div dir="rtl">بنام خدا</div>

###### top

- [Single Configuration](#single-configuration)
  - [Zookeeper](#zookeeper)
  - [Topic](#topic)
  - [Broker](#brker)
  - [Produser](#produser)
  - [Consumer](#consumer)
- [Cluster Configuration](#cluster-cinfiguration)
- [](#)
- [](#)
- [](#)
  
  
  
[Top](#top)

# Single Configuration
## Zookeeper
Kafka uses [ZooKeeper](https://zookeeper.apache.org/)
```vala
  bin/zookeeper-server-start.sh config/zookeeper.properties
```
then we can start kafka:
```vim
  bin/kafka-server-start.sh config/server.properties
```
## Topic
- Topic Properties:
  1. Name:
  2. Partition:
  3. Replication:
  
- Create Topic:
```vim
  bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
```
- Query of existing Topic:
  1. One:
  ```vim
    bin/kafka-topics.sh --list --zookeeper localhost:2181
  ```
  2. Two:
  ```vim
    bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic test
  ```
  
## Broker
in _config/server.properties_ file we find these configs:
```vim
  broker.id=0
  listeners=PLAINTEXT://:9092
  log.dir=/tmp/kafka-logs
```
to make next broker, we should increase id,port,logName incerementaly with brokerName.
for example the server1.properties for broker1 will be:
```vim
  broker.id=1
  listeners=PLAINTEXT://:9093
  log.dir=/tmp/kafka-logs-1
```

## Produser
Produser coming for testing, it could send message to Consumer
```vim
  bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
  // after this command you could send message from terminal
```

## Consumer
Consumer used to dump of inputing messaging.
```vim
  bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
```

[Top](#top)
# Cluster Configuration
1. First Install(untar) Kafka in the same path in all servers.
2. assume ServerNames are like: NameiD-Server
3. in Zookeeper config(zookeeper.properties) in all Servars:
```vim
  dataDir=/var/zookeeper/data  # Should define this path in all Server
  clientPort=2181
  maxClientCnxns=0
  server.1=Name1-Server:2888:3888
  server.2=Name2-Server:2888:3888
  server.3=Name3-Server:2888:3888
  ...
  initLimit=5
  syncLimit=2
```
4. Add ServerId in All Server under Zookeeper Path:
```vim
  echo "Id" > /var/zookeeper/data/serverid
```
5. Change server.config File for Kafka configuration in all server:
```vim
  broker.id=[BROKER_ID]
  log.dirs=/data/kafka/kafka-logs
  zookeeper.connect=Name1-Servers:2181,Name2-Servers:2181,Name3-Servers:2181,...
```
6. Start Zookeeper on All Servers:
```vim
  nohup bin/zookeeper-server-start.sh config/zookeeper.properties &
```
7. also start Kafka on All machine:
```vim
  nohup bin/kafka-server-start.sh config/server.properties &
```

[Top](#top)
#

[Top](#top)
#

[Top](#top)
#

