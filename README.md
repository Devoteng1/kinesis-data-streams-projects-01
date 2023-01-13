# kinesis-data-streams-projects-01

# Overview

In this project qw will be creating a simple Amazon Kinesis application and using the AWS CLI to put records into the stream and read to check records in the streams

Amazon Kinesis Data Streams is a serverless streaming data service that makes it easy to capture, process, and store data streams at any scale.

Some features
- Data inserted into Kinesis data stream can’t be deleted ( Data retention period 24 hours(default) but can be increased) 
- Records with the same partition goes into the same shard
- Producers: AWS SDK, Kinesis Producer Library (KPL), Kinesis Agent
- Consumers: AWS SDK, Kinesis client Library (KCL), Kinesis Data Firehose, Kinesis Data Analytics

Amazon Kinesis Data Streams Capacity Modes
- Provisioned mode: You can choose the number of shards provisioned, scale manually or using API, send 1MB/S of data to shard and get 2MB/S out of shard
- On-demand: No need to provision or manage the capacity. Provisioned capacity defaults to 4MB/S of data in or 40000 records per second

# Intructions 

# Stage 1 - Create Amazon Kinesis Application

Head to the Amazon Kinesis dashboard
