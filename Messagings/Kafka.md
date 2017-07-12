<div dir="rtl">بنام خدا</div>

###### top

- [Single Configuration](#single-configuration)
  - [Zookeeper](#zookeeper)
  - [Topic](#topic)
  - [Broker](#brker)
  - [Produser](#produser)
  - [Consumer](#consumer)
- [Cluster Configuration](#)
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
1. 

[Top](#top)
#

[Top](#top)
#

[Top](#top)
#

