# Distributed Event Streaming Platform Components
Events  describe an entity's ovservable state updates over time
- GPS coordinates of a car
- Temperature of a room
- Blood pressure of a patient

Common format
- primitive: hello
- key value pair
- key value pair with timestamp

One source to one destination: Event streaming from one event source(sensors, devices, ...) to one destination (event destination)

Event streaming platform (ESP)

![image](/pics/esp.png)

ESP conponent

![image](/pics/esp_component.png)
- Event broker: contains ingester, processor, consumption

Popular ESPs: amazon kinesis, apache kafka, apache flink, apache storm, apache spark

# Kafaka Overview
![image](/pics/kafka_structure.png)

Main feature:
- Distribution system
- Highly scalable
- Highly reliable
- Permanent persistency
- Open source

Event streaming as a service: several commercial service providers offer an on-demand ESP-as-a-Service to meet your streaming requirements. Many of them are built on top of Kafka and provide added value for customers
- Confluent Cloud
- IBM Event Streams
- Amazon MSK

# Building Event Streaming Pipelines using Kafka
Broker: A Kafka cluster contains one or many **brokers**. You may think of a Kafka broker as a dedicated server to receive, store, process, and distribute events. Brokers are synchronized and managed by another dedicated server called ZooKeeper. Each broker contains one or many topics. You can think of a topic as a database to store specific types of events, such as logs, transactions, and metrics, for example. Brokers manage to save published events into topics and distribute the events to subscribed consumers. 

![image](/pics/broker.png)

Partition and replication: It uses topic partitions and replications to increase fault-tolerance and throughput so that event publication and consumption can be done in parallel with multiple brokers. In addition, even if some brokers are down, Kafka clients are still able to work with the target topics replicated in other working brokers. For example: A log topic has been separated into two partitions: 0, 1, and a user topic has been separated into two partitions: 0, 1.

![image](/pics/partition_replications.png)

Kafka topic CLI

![image](/pics/kafka_cli.png)

Kafka producer
- Client applications that publish events to topic partition
- An event can be optionally associated with a key
- Events assocaited with the same key will be published to the same topic partition
- Events not associaated with any key will be published to topic partitions in rotation

Kafka producer in action

![image](/pics/kafka_producer_in_action.png)

Kafka producer CLI

![image](/pics/kafka_producer_cli.png)


Kafka consumer
- Consumers are clients subscribed to topics
- Consume data in the same order
- Store an offset record for each partition
- Offset can be reset to zero to read all events from the beginning again

Kafka consumer in action

![image](/pics/kafka_consumer_in_action.png)

Kafka consumer CLI

![image](/pics/kafka_consumer_cli.png)

Example

![image](/pics/kafka_example.png)


Summary

![image](/pics/kafka_core_summary.png)
