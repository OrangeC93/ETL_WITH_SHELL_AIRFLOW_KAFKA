# ETL Fundamentals
Extraction
- Web scraping or APIs
- Static or streaming online

Transformation
- Cleaning, Filtering, Joining, Featuring enginering, Formatting and Data Typing

Loading
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
Web scraping, APIs, querying, Edge computing, Biomedical devices
# Data Transform Techs
Data typing, Data structing, Anonymizing, Encrypting

- Cleaning: duplicate records, missing values
- Normalizing: converting data to common units
- Filtering, sorting, aggregating, binnign

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

  

