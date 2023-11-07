## AWS WorkSpaces
> Managed desktop as a Service (DaaS) solution to easily provision Windows or Linux desktops
> Great to eliminate management of on-prem VDI(Virdual Desktop Infra)
> Fast and quickly scalable to thousands of users
> Secured data - integrates with KMS
> Pay-as-you-go service with monthly or hourly rates\
> ![image](<images/Pasted image 20231031233819.png>)
### Amazon WorkSpaces-Multiple Regions
> Minimizing latencies for WorkSpaces
> Setup to closer locations to users.\
> ![image](<images/Pasted image 20231031233957.png>)

## Amazon AppStream 2.0
> Desktop app Streaming Service
> Deliver to any computer; without acquiring, provisioning infrastructure
> The app is delivered from within a web browser\
> ![image](<images/Pasted image 20231031234100.png>) 

### AppStream 2.0 vs WorkSpaces
- Workspaces
> Fully managed VDI and desktop available
> The users connect to the VDI and open naive or WAM apps
> Workspaces are on-demand or always on
- Appstream 2.0
> Stream a desktop app to web browsers (no need to connect to a VDI)
> Allow to configure an instance type per app type (CPU, RAM, GPU)

## Amazon IoT Core
> Allow you to easily connect IoT devices to the AWS Cloud
> Serverless, secure and scalable to bilions of devices and trillions of messages
> Your apps can communicate with your devices when they arent connected
> Integrates with a low of AWS services
> Build  IoT apps that gather, process, analyze and act on data\
> ![image](<images/Pasted image 20231031234935.png>)

## Amazon Elastic Transcoder
> Used to convert media files stored in S3 into media files in the formats required by consumer 
playback devices
> Benefits:
> 	- Easy to use
> 	- Highly scalable - duration based pricing model
> 	- Cost effective - duration-based pricing model
> 	- Fully managed & secure, pay for what you use\
>![image](<images/Pasted image 20231031235116.png>)

## Amazon AppSync
> Store and sync data across mobile and web apps in real-time
> Makes use of GraphQL (mobile technology from Facebook)
> Client Code can be generated automatically
> Integrations with DynamoDB / Lambda
> Real-time subscriptions
> Offline data synchronization (replaces Cognito Sync)
> Fine Grained Security
> AWS Amplify can leverage AWS AppSync in the background

## AWS Amplify
> A set of tools and services that helps you develop and deploy scalable full stack web and mobile 
apps
> You can manage Authentication, Storage, API (REST, GraphQL), CI/CD, PubSub, Analytics, AI/ML Predictions, Monitoring, Code from AWS, Github, etc..\
> ![image](<images/Pasted image 20231031235750.png>)

## AWS Device Farm
> Fully-managed service that tests you web and mobile apps against desktop browser, real mobile
devices and tablets
> Run tests concurrently on multiple devices (speed up execution)
> Ability to configure device settings (GPS, Language, Wi-FI, Bluetooth)\
> ![image](<images/Pasted image 20231031235938.png>)

## AWS Backup
> Fully-managed service to centrally manage and automate backups across AWS services
> On-demand and scheduled backups
> Support PITR (Point in time Recovery)
> Retention Periods, Lifecycle Management, Backup Policies
> Cross-Region Backup
> Cross-Account Backup (using AWS Organizations)\
> ![image](<images/Pasted image 20231101000151.png>)

## Disaster Recovery Strategies
> Exam asks which one is cheapest?
> 	- The answer is **Backup and Restore**\
> ![image](<images/Pasted image 20231101000343.png>)\
> ![image](<images/Pasted image 20231101000429.png>)

>![image](<images/Pasted image 20231101000512.png>)

## AWS Elastic Disaster Recovery (DRS)
> Used to be named CloudEndure Disaster Recovery
> Quickly and easily recover your physical, virtual, and cloud-based servers into AWS
> Example: protect your most critical dbs(including Oracle MySQL, and SQL server) enterprise APPs, 
protect your data from ransomware attacks
> Continuous block-level replication for your servers\
> ![image](<images/Pasted image 20231101000829.png>)

## AWS DataSync
> Move large amount of data from on-prem to AWS
> Can synchronize to Amazon S3 (any storage classes - including Glacier), Amazon EFS, Amazon FSx 
for Windows.
> Replication tasks can be scheduled hourly, daily, weekly
> The replication tasks are incremental after the first full load\
> ![image](<images/Pasted image 20231101001028.png>)

## AWS App Discovery Service
> Plan migration projects by gathering information about on-prem data centers
> Server utilization data and dependency mapping are important for migrations

#### Agentless Discovery(AWS Agentless Discovery Connector)
> VM inventory, configuration, and performance history such as CPU, memory, and disk usage

#### Agent-based Discovery(AWS Application Discovery Agent)
> System configuration, system performance, running processes and details of the network
connections between systems

> Resulting data can be viewed with AWS Migration Hub

### AWS Application Migration Service (MGN)
> Lift and Shift solution which simplify migration apps to AWS
> Converts your physical, virtual and cloud-based servers to run natively on AWS
> Supports wide range of platforms, OS and dbs
> Minimal downtime, lower cost\
> ![image](<images/Pasted image 20231101001625.png>)

## AWS Migration Evaluator
> Helps you build a data-driven business case for migration to AWS
> Provides a clear baseline of what you organization is running today
> Install Agentless Collector to conduct broad-based discovery
> Take a snapshot of on-prem foot-pring, server dependencies
> Analyze current state, define target state, then develop migration plan\
> ![image](<images/Pasted image 20231101001918.png>)

## AWS Migration Hub
> Central Location to collect servers and apps inventory data for the assessment, planning and tracking of migrations to AWS
> Helps accelerate your migration to AWS, automate lift-and-shift
> AWS Migration Hub Orchestrator - provides pre-build templates to save time and effort migration 
enterprise apps
> Supports migrations status updates from Application Migration Service(MGN) and Database
Migration Service (DMS)

## AWS Fault Injection Simulator (FIS)
>A fully managed service for running fault injection experiments on AWS workloads
>Based on Chaos Engineering - stressing an application by creating disruptive events observing how the system responds and implementing improvements
>Helps you uncover hidden bugs and performance bottlenecks
>Supports the following AWS services: EC2, ECS, EKS, RDS
>Use pre-build templates that generate the desired disruptions.\
>![image](<images/Pasted image 20231101002353.png>)

## AWS Step Functions
> Build serverless visual workflow to ochestrate your Lambda funcs
> Features: sequence, parallel, conditions, timeouts, error handlings.
> Can integrate with EC2, ECS, On-prem servers, API Gateway, SQS queues.
> Possibility of implementing human approval feature
> Use cases: order fulfillment, data processing, web apps, any workflow\
> ![image](<images/Pasted image 20231101002547.png>)

## AWS Ground Station
> Fully managed service that lets you control satellite communications, process data and scale your
satellite operations.
> Allows you to download satellite data to your AWS VPC within seconds.
> Send satellite data to S3 or EC2 instance
> Use cases: forecasting, surface imaging, communications, video broadcasts\
> ![image](<images/Pasted image 20231101002712.png>)

## Amazon Pinpoint
> Scalable 2-way (outbound/inbound) marketing communications service
> Supports email, SMS, push, voice, and in-app messaging
> Ability to segment and personalize messages with the right content to customers
> Possibility to receive replies
> Scales to billions of messages per day
> Use cases: run campaigns by sending marketing, bulk, transactional SMS messages
> Versus Amazon SNS or Amazon SES
> 	- In SNS and SES you managed each message's audience, content and delivery schedule
> 	- In Amazon Pinpoint, you create message templates delivery schedules, highly targeted segments and full campaigns

