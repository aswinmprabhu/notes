---
id: 1445f443-eb7c-43f5-9fa0-ddb7dc10c487
---

# Kafka Internals
#Omnivore

[Read on Omnivore](https://omnivore.app/me/kafka-internals-1852b397db4)
[Read Original](https://engineering.cred.club/kafka-internals-47e594e3f006)

## Highlights

> Apache Kafka is a distributed pub/sub messaging system where producers can publish messages to Kafka and consumers can subscribe to certain classes of messages and consume them. It is often regarded as a distributed commit log since messages published to Kafka are stored reliably in order until the retention period.
> Message: Message is a record of information. Each message has an optional key which is used for routing the message to appropriate partition in a topic, a mandatory value which is the actual information. [⤴️](https://omnivore.app/me/kafka-internals-1852b397db4#eb45ebe7-57dd-4550-bf82-6e47063e6758)  ^eb45ebe7

> Broker: Broker is an application that is responsible for persisting messages. Consumers interact with the broker to consume messages published to topics. [⤴️](https://omnivore.app/me/kafka-internals-1852b397db4#2a3b9317-75b2-4781-8e28-00b7dd6b9449)  ^2a3b9317

> Topic: Topic is used for classification of messages into logical groups.
> Partition: Each topic is divided into multiple partitions. Each partition is replicated across a configurable number of brokers to handle redundancy and scalability. Each partition has one leader which is responsible for reads and writes and zero or more followers which replicate the leader.
> Offset: Each message is uniquely identified by a topic, partition it belongs and the offset number. Offset is a continually increasing integer that identifies a message uniquely given a topic and a partition. Messages are ordered within a partition by offset number. [⤴️](https://omnivore.app/me/kafka-internals-1852b397db4#71a14d30-8205-4927-a7d5-0d8205f2e0f2)  ^71a14d30

> If the partition number is passed as an input, it is used as the partition.
> If the message has a key, it uses the default partitioner (which takes the hash of the key modulo number of partitions ) to decide the partition. We can also implement our own custom partitioner.
> If the message key is not specified, then the producer randomly distributes the messages across partitions using the round-robin algorithm. [⤴️](https://omnivore.app/me/kafka-internals-1852b397db4#ab70b391-6ac0-4b4b-ad12-25b084fb7820)  ^ab70b391

