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

