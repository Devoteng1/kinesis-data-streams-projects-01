# kinesis-data-streams-projects-01

# Overview

In this project we will be creating a simple Amazon Kinesis application and using the AWS CLI to put records into the stream and read to check records in the streams

Amazon Kinesis Data Streams is a serverless streaming data service that makes it easy to capture, process, and store data streams at any scale.

Some features
- Data inserted into Kinesis data stream can’t be deleted ( Data retention period 24 hours(default) but can be increased) 
- Records with the same partition goes into the same shard
- Producers: AWS SDK, Kinesis Producer Library (KPL), Kinesis Agent
- Consumers: AWS SDK, Kinesis client Library (KCL), Kinesis Data Firehose, Kinesis Data Analytics

Amazon Kinesis Data Streams Capacity Modes
- Provisioned mode: You can choose the number of shards provisioned, scale manually or using API, send 1MB/S of data to shard and get 2MB/S out of shard
- On-demand: No need to provision or manage the capacity. Provisioned capacity maximum 200MiB/second write capacity and maximum 400 MiB/second read capacity

# Intructions 

# Stage 1 - Create Amazon Kinesis Application

Head to the Amazon Kinesis Services dashboard to create a Kinesis Data Stream . 
We have three options : Kinesis Data Stream, Kinesis Data Fireshose and Kinesis Data Analytics
Select Kinesis Data Stream and clich on Create data stream

Enter a name for your stream. In this tutirial, we will call our stream "DemoStream"

For the capacity mode : Select Provisioned mode and number od shards value set to 1 which can be increased or describe later

Click on create stream to get our stream created. You can wait for just some few seconds to get the stream created

Afterwards our stream should be in the "Active" state.

# Stage 2 - Create a producer to put records into the Kinesis Data Stream


