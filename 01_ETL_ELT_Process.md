# ETL Fundamentals
Extraction: first stage of the ETL process, where data is acquired from various source systems. The data may be completely raw, such as sensor data from IoT devices, or perhaps it is unstructured data from scanned medical documents or company emails. It may be streaming data coming from a social media network or near real-time stock market buy/sell transactions, or it may come from existing enterprise databases and data warehouses.
- Web scraping or APIs
- Static or streaming online

Transformation: The transformation stage is where rules and processes are applied to the data to prepare it for loading into the target system. This is normally done in an intermediate working environment called a “staging area.” Here, the data are cleaned to ensure reliability and conformed to ensure compatibility with the target system.  
- Cleaning, Filtering, Joining, Featuring enginering, Formatting and Data Typing

Loading: The load phase is all about writing the transformed data to a target system. The system can be as simple as a comma-separated file, which is essentially just a table of data like an Excel spreadsheet. The target can also be a database, which may be part of a much more elaborate system, such as a data warehouse, a data mart, data lake, or some other unified, centralized data store forming the basis for analysis, modeling, and data-driven decision making by business analysts, managers, executives, data scientists, and users at all levels of the enterprise.
- Database, Data warehouse, Data mart

Usecase
- Digitizing analog media
- Moving data from OLTP system to OLAP system
- ML
- Dashboard

# ELT Basics
Usecase
- Demanding scalability requirements of Big Data
- Streaming analytics
- Integration of highly dsitributed data sources
- Multiple data products from the same sources

# Comapring ELT to ELT
ELT is emerging
- Big Data
- More flexibility: end users build their own transformations
- No information loss
- ELT separates the data pipeline from the processing

# Data Exaction Techs
Web scraping, APIs, querying, Edge computing(extracting features of interest from the raw data), Biomedical devices

# Data Transform Techs
Data typing, Data structing, Anonymizing, Encrypting

- Cleaning: duplicate records, missing values
- Normalizing: converting data to common units
- Filtering, sorting, aggregating, bining

Examples of ways information can be lost in transformation proceses include:
- Lossy data comppression: For example, converting floating point values to integers, reducing bitrates on audio or video.
- Filtering: For example, filtering is usually a temporary selection of a subset of data, but when it is permanent, information can easily be discarded
- Aggregation: For example, average yearly sales vs. daily or monthly average sales
- Edge computing devices: For example, false negatives in surveillance devices designed to only stream alarm signals, not the raw data

# Data Loading Techs
- Full
  - Start tracking transactions in a new data warehouse
  - Used for porting over transaction history
- Incremental
  - Data is appended to, not overwritten
  - Used for accumulating transaction history
  - Depending on the volume and velocity of data, can be batch loaded or stream loaded
- Scheduled
  - Periodic loeading, like daily transactions to database
  - Windows Task Scheduler, cron
- On-demand, triggered by
  - Measures such as data size
  - Event detection, like motion, sound or temperature change
  - User requests, like video or music streaming, webpages
- Batch and Stream
  - Batch: periodic updates using window of data
  - Stream: continuous updats as data arrives
  - Micro-batch: short time windows used to access older data
- Pull and Push:
  - Pull: requests for data originate from the clident, RSS feeds, email
  - Push: server pushes data to clients, notifications, instant messaging
- Parallel and serial
  - Multiple data streams 

  

