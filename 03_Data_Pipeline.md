# Introduction of Data Pipeline


# Key Data Pipeline Processes
Data pipeline processes:
- Loading into destination
- Scheduling or Triggering
- Monitoring
- Maintenance and Optimization

Data pipeline performance: 
- latency: the time it takes for data packets to flow through the pipeline
- throughput: the volume of data passing through the pipeline over time
- warning, errors, failures: caused by factors such as network overloading, and failures at the source or destination systems
- utilization rate: how fully the pipeline's resources are being utilized, which affects cost
- logging and alerting: alerting administrators when failures occur

Load balanced pipelines
- Just in time data packet relays: the stage is never left to idle while the pipeline is operating
- No upstream data flow bottlenecks
- Uniform packet throughput for each stage

Handling unbalanced loads
- slower stages **parallelized** to speed up throughput
- processes can be replicated on multiple cpu/cores/threads

Stage synchornization: further synchronization between stages is likely still possible, and a typical solution is to include input and output, or I/O buffers as needed to smooth out the flow of data. An I/O buffer is a holding area for data, placed between processing stages having different or varying delays. Buffers can also be used to regulate the output of stages having variable processing rates, and thus may be used to improve throughput. Single input and output buffers are also used to distribute and gather loads on parallelized stages.
- **I/O** buffers can help synchoronize stages
- Holding area for data between processing stages
- Buffers regulate the flow of data, may improve throughput
- I/O buffers used to distribute loads on parallelized stages

# Batch vs Streaming
Batch data piplines:
- operate on batches of data
- usually run periodically
- can be initiated based on data size or other triggers
- when latest data isn't needed
- typical choie when accuracy is critical

Streaming data pipeline
- Ingest data packets in rapid succession
- For real-time results
- Records/events processed as they happen
- Event streams can be loaded to storage
- Users publish/subscribe to event streams

Micro-batch data pipelines
- Tiny micro-batches and faster processing simulate real-time processing
- Smaller batches improve load balancing, lower latency
- When short windows of data are required

Batch vs stream:
- accuracy vs latency

Lambda architecture
- data stream fills in latency gap
- used when data window is needed but speed is critical
- drawback is logical complexity
- lambda architecture = accuracy and speed
![image](pics/lambda_architecture.png)


Batch data pipeline use cases
- data backups
- trasaction history loading
- billing and order processing
- data modelling
- forecasting

Stream use cases
- wathing movies, music, podcasts
- social media feeds, sentiment analytics
- fraud detection
- user behavior, advertising
- stock market trading
- read time product pricing
