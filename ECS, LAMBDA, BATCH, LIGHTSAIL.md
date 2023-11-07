
## ECS(Elastic Container Service)
> Launch<mark style="background: #FFB8EBA6;"> docker containers on AWS</mark>
> You <mark style="background: #FFB8EBA6;">must provision</mark> & maintain the infra(the <mark style="background: #FFB8EBA6;">EC2</mark> instance)
> AWS takes care of starting / stopping containers
> Has <mark style="background: #FFB8EBA6;">integrations with the Application Load Balancer</mark>\
> ![image](<images/Pasted image 20230913224808.png>)

## Fargate
> Launch <mark style="background: #FFB8EBA6;">docker containers on AWS</mark>
> You <mark style="background: #FFB8EBA6;">do not provision</mark> the infra (no <mark style="background: #FFB8EBA6;">EC2</mark> instances to manage) - simpler
> <mark style="background: #FFB8EBA6;">Serverless</mark> offering
> AWS just runs containers for you based on the CPU /
RAM you need.\
![image](<images/Pasted image 20230913224946.png>)

## ECR(Elastic Container Registry)
> <mark style="background: #FFB8EBA6;">Private Docker registry</mark> on AWS
> This is where you store your Docker images so they can
be run by ECS or Fargate.\
> ![image](<images/Pasted image 20230913225130.png>)

## What is serverless?
> Devs dont have to manage servers anymore
> They just deploy code
> They just deploy functions
> Initially Serverss == FaaS (Function as a Service)
> Serverless was pioneered by AWS Lambda but now also
includes anythin thats managed "database, messaging, storage, etc.."
> Serverless does not mean there are no servers it means you just dont manage / provision / see them.
> So far in this course:
> 	- S3 --> Storage
> 	- DynamoDB --> DB
> 	- Fargate --> Containers

## Lambda
> Lambda is reactive type of service
### Why AWS Lambda
> <mark style="background: #FFB8EBA6;">Virtual functions</mark> - no servers to manage
> Limited by time - short executions
> Run <mark style="background: #FFB8EBA6;">on-demand</mark>
> <mark style="background: #FFB8EBA6;">Scaling is automated</mark>\
![image](<images/Pasted image 20230913230001.png>)

### Benefits of AWS Lambda
> Easy <mark style="background: #FFB8EBA6;">pricing</mark>: 
>> <mark style="background: #FFB8EBA6;">Pay per request and compute time</mark>
> Free tier of 1,000,000 AWS Lambda Requests and 400,000 GBs of compute time
> Integrated with the whole AWS suite of services
> **Event-Driven**: Functions geet invoked by AWS when needed
> Integrated with through with many programming languages
> <mark style="background: #FFB8EBA6;">Easy monitoring</mark> through <mark style="background: #FFB8EBA6;">AWS CloudWatch</mark>
> <mark style="background: #FFB8EBA6;">Easy to get more resources</mark> per functions (up to 10GB of RAM)
> Increasing RAM will also improve CPU and network quality

### AWS Lambda language support
> ![image](<images/Pasted image 20230913230435.png>)

### Example: Serverless Thumbnail Creation
>![image](<images/Pasted image 20230913230546.png>)

### Example: Serverless CRON job
>
> ![image](<images/Pasted image 20230913230746.png>)

### Pricing: Lambda
> ![image](<images/Pasted image 20230913230906.png>)

## Amazon API Gateway
> <mark style="background: #FFB8EBA6;">Building serverless API</mark>
>  Fully managed service for devs to easily create,
publish, maintain, monitor and secure APIs.
> Serverless and scalable
><mark style="background: #FFB8EBA6;"> Supports RESTful APIs</mark> and WebSocket APIs
> Support for security, user auth, API throttling, API keys,
monitoring.\
> ![image](<images/Pasted image 20230913232908.png>)
 
## AWS Batch
> Fully managed batch processing at any scale
> Efficiently run 100,000s of computing batch jobs on
AWS
> A batch job is a job with a start and an end(opposed to
continuos)
> Batch will dynamically launch EC2 instances or Spot
Instances
> AWS Batch provisions the right amount of compute /
memory
> You submit or schedule batch jobs and AWS Batch does
the rest
> Batch jobs are defined as Docker images and run on
ECS
![image](<images/Pasted image 20230913233358.png>)
### Batch vs Lambda
> Lambda:
>> Time limit
>> Limited runtmes
>> Limited temprorary disk space
>> Serverless
> Batch
>> No time limit
>> Any runtime as long as its packaged as docker image
>> Rely on EBS / instance stora for disk space
>> Relies on EC2(can be managed by AWS)


## Lightsail
> Virtual servers, storage, databases and networking
> Low & predictable pricing
> Simpler alternative to using EC2, RDS, ELB, EBS, Route 53
> Great for people with little cloud expreince
> Can setup notifications and monitoring of your Lightsail resources
> Use cases:
>> Simple web apps
>> Websites
>> Dev / Test env
> Has HA but no auto-scaling, limited AWS integrations


## SUMMARY
> Docker
> ECS: run docker containers on EC2 instances
> Fargete:
>> Serverless
>> Without provision EC2 run docker containers
> ECR : Private docker images registry
> Batch: run batch jobs on AWS across managed EC2 instances
> Lightsail: Predictable & low pricing simple apps
> Lambda:
>> Lambda is serverless, FaaS, seemless scaling, reactive
>> Lambda billing:
>>> By the time run x by the RAM provisioned
>>> By the number of invocations
>> Language support
>> Invocation time: up to 15 minitus
>> Use cases:
>>> Create Thumbnails for images uploaded into S3
>>> cron job
>> **API Gateway**: expose Lambda functions as HTTP API. 

