> When we start deploying multiple apps they will
inevitably need to communicate with one anoteher
> There are two patterns of app communication\
>  ![image](<images/Pasted image 20230919220140.png>)\
>  Synchronous between apps can be problematic if there are sudden spikes of trafic
>  What if you need to suddenly encode 1000 videos but usually its 10
>  In that case its better to decouple you apps:
>> using SQS: queue model
>> using SNS: pub/sub model
>> using Kinesis: real-time data streaming model
> These services can scale indepently from our app.

## SQS - Simple Queue Service
> ![image](<images/Pasted image 20230919220500.png>)

### SQS - Standard Queue
> Oldest AWS offering
> Fully managed (serverless) use to decouple apps
> Scales from 1 message per second to 10,000s per
second
> Default retention of messages: 4days, maximum of 14
days
> Messages are deleted after the are read by consumers
> Low latency
> Consumers share the work to read messages & scale
horizontally\
> ![image](<images/Pasted image 20230919220845.png>)
> 
### FIFO Queue
> First in first out

## Kinesis 
> Real-time big data streaming
> Managed service to collect, process and analyze real-time streaming data at any scale
> Too detailed for the Cloud Practioner exam but good to
know:
>> Kinesis data streams: low latency streaming to ingest
>data at scale from hundreds of thousands of sources
>> Kinesis Data Firehose: load streams into S3, redshift,
>ElasticSearch
>> Kinesis Data analytics: perform real-time analytics on
>streams using SQL
>> Kinesis Video Streams: monitor real-time video
>streams for analytics or ML\
>![image](<images/Pasted image 20230919221656.png>)

## SNS - Simple Notifaction Service
> Pub-Sub model
> One message to many receivers\
> ![image](<images/Pasted image 20230919221830.png>)\
> The event publishers only sends message to one SNS
topic
> As many event subs as we want to listen to the SNS topic notifactions
> Each sub to the topic will get all the messages
> Up to 12,500,500 sub per topic, 100,000 topics limit\
> ![image](<images/Pasted image 20230919222510.png>)

## Amazon MQ
> SQS, SNS are cloud-native
> Traditional apps running from on-prem may use open
protocols such as: MQTT, AMQP, STOMP, Openwire, WSS.
> When migration to the cloud, instead of re-engineering the pp to use SQS and SNS, we can use Amazon MQ
> AmazonMQ is managed message broker service for
RabbitMQ and ActiveMQ
> Amazon MQ doesnt scale as much SQS/SNS
> Amazon MQ runs on servers, can run in Multi-AZ with
failover
> Amazon MQ has bot queue feature and topic features

## SUMMARY
> SQS: Queue services, multiple producers, multiple
consumers, decouple apps, messages are kept up to 14 days
> SNS: Notification service, pub-sub, multi subs to one
topic, no message retention
> Kinesis: real-time data streaming, persistence and
analysis
> Amazon MQ: managed message broker for ActiveMQ
and rabbitMQ in the cloud.

