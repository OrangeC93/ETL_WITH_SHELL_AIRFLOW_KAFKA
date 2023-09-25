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

# Kafka Streaming
Kafka Streams API
- Simple client library to facilitate data processing in event streaming pipelines
- Processes and analyzes data stored in kafaka topic
- Record only processed once
- Processing one record at a time

Stream processing topology:
- There are two special types of processors: On the left, you can see the source processor which has no upstream processors. A source processor acts like a consumer which consumes streams from Kafka topics and forwards the processed streams to its downstream processors. On the right, you can see the sink processor, which has no downstream processors. A sink processor acts like a producer which publishes the received stream to a Kafka topic

![image](/pics/stream_process_topology.png)

Example

![image](/pics/weather_stream_example.png)

# Lab - terminal
download Kafka + unzip
```
wget https://archive.apache.org/dist/kafka/2.8.0/kafka_2.12-2.8.0.tgz
tar -xzf kafka_2.12-2.8.0.tgz
```

start zoomkeeper
```
cd kafka_2.12-2.8.0
bin/zookeeper-server-start.sh config/zookeeper.properties
```

create topic
```
cd kafka_2.12-2.8.0
bin/kafka-topics.sh --create --topic news --bootstrap-server localhost:9092
```

producer send data
```
bin/kafka-console-producer.sh --topic news --bootstrap-server localhost:9092

Good morning
Good day
Enjoy the Kafka lab
```

consumer: listen to the messages in the topic news
```
cd kafka_2.12-2.8.0
bin/kafka-console-consumer.sh --topic news --from-beginning --bootstrap-server localhost:9092
```
# Lab - python
```
pip install kafka-python

# KafkaAdminClient class is to enable fundamental administrative management operations on kafka server such as creating/deleting topic, retrieving, and updating topic configurations and so on.

admin_client = KafkaAdminClient(bootstrap_servers="localhost:9092", client_id='test')
# bootstrap_servers="localhost:9092" argument specifies the host/IP and port that the consumer should contact to bootstrap initial cluster metadata
# client_id specifies an id of current admin client


# Create new topics
topic_list = []
new_topic = NewTopic(name="bankbranch", num_partitions= 2, replication_factor=1)
topic_list.append(new_topic)
admin_client.create_topics(new_topics=topic_list)
# Equals to terminal 
"kafka-topics.sh --bootstrap-server localhost:9092 --create --topic bankbranch  --partitions 2 --replication_factor 1"

# Describe a topic
configs = admin_client.describe_configs(
    config_resources=[ConfigResource(ConfigResourceType.TOPIC, "bankbranch")])
# Equals to terminal 
kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic bankbranch

# Define producer
# For the value_serializer argument, we define a lambda function to take a Python dict/list object and serialize it into bytes.
producer = KafkaProducer(value_serializer=lambda v: json.dumps(v).encode('utf-8'))
producer.send("bankbranch", {'atmid':1, 'transid':100})
producer.send("bankbranch", {'atmid':2, 'transid':101})
# Equals to terminal
kafka-console-producer.sh --bootstrap-server localhost:9092 --topic bankbranch

# Define consumer
consumer = KafkaConsumer('bankbranch')
# Once the consumer is created, it will receive all available messages from the topic bankbranch. Then we
can iterate and print them with the following code snippet:
for msg in consumer:
    print(msg.value.decode("utf-8"))
# Equals to terminal
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic bankbranch
```
