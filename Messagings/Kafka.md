<div dir="rtl">بنام خدا</div>

###### top

- [Configuration](#configuration)
  - [Zookeeper](#zookeeper)
  - [Topic](#topic)
  - [Broker](#brker)
- [](#)
- [](#)
- [](#)
- [](#)
  
  
  
[Top](#top)
# Configuration
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
```vim
  bin/kafka-topics.sh --list --zookeeper localhost:2181
```

## Broker



[Top](#top)
#


[Top](#top)
#

