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
We have three options : **Kinesis Data Stream** , **Kinesis Data Fireshose** and **Kinesis Data Analytics**
Select **Kinesis Data Stream** 
click on **Create data stream**

Enter a name for your Kinesis Stream. In this tutirial, we will call our stream **"DemoStream"**

For the capacity mode : Select **Provisioned mode** 
Set the number of shards value **1** which can be increased or describe later

Click on **Create Stream** to create the stream. You can wait for just some few seconds to get the stream created

Afterwards our stream should be in the **"Active" state**.

# Stage 2 - Create a producer to put records into the Kinesis Data Stream
In this tuotorial we are going to use the AWS CLI to communicate with the Amazon Kinesis Service

This tutorials assume you have already installed and configured AWS CLI.
You can follow this Documentation [https://docs.aws.amazon.com/cli/v1/userguide/install-windows.html] to install and configure the AWS CLI for your OS. We are using windows 10 for this tutorial. 

To confirm AWS CLI has been installed and configure on your computer, you can check the installed version by typing "**aws -version**" which should print the version 
of AWS CLI installed.

We can view a list of avaialable commands by typing **aws kinesis help**

Let's check the list of created Kinesis Data Streams in our account by typing  **aws kinesis list-streams**

Now lets put some records into the stream. 
We can use the **PutRecord** to put one record into the stream or **PutRecords** to put many records into the stream

We are going to simulate data coming from a BANK ATM whose data has to be streammed into Kinesis Data Streams for further processing. 

We can use the command below to send a record to the stream.
<pre >

 - aws kinesis  **put-record**\                                    put-record used to put a single record into the stream

 - --stream-name  **DemoStream**\                                   We are passing in the name of our created stream. In this case **DemoStream**

 - --partition-key  **1**\                                          We are defining a partition key for this put operation

 - --cli-binary-format  **raw-in-base64-out**\                      A flag that specifies how the binary input paramaters should be interpreted. In this case **raw-in-                                                                     base64-out**

 - --data **"{'trans_id': 1, 'trans_type': 'ATM', 'amt': 200}"**    The data blob to be put into the stream. In this case **"{'trans_id': 1, 'trans_type': 'ATM' ,                                                                         'amt':200}"**
 <pre />
 


In this example we are using the PutRecord API to put 4 records into the stream one by one. Its also possible to use the PutRecords API to write many records at once   to the stream 
 1. aws kinesis put-record --stream-name DemoStream --partition-key 1 --cli-binary-format raw-in-base64-out --data "{"trans_id": 1, "trans_type": "ATM", "amt":   200}"
 2. aws kinesis put-record --stream-name DemoStream --partition-key 1 --cli-binary-format raw-in-base64-out --data "{"trans_id": 2, "trans_type": "ATM", "amt":   400}"
 3. aws kinesis put-record --stream-name DemoStream --partition-key 1 --cli-binary-format raw-in-base64-out --data "{"trans_id": 3, "trans_type": "ATM", "amt":   600}"
 4. aws kinesis put-record --stream-name DemoStream --partition-key 1 --cli-binary-format raw-in-base64-out --data "{"trans_id": 4, "trans_type": "ATM", "amt":   900}"
 
 






