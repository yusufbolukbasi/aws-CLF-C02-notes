### RELATIONAL DATABASES

> Linked databases
>  ![image](<images/Pasted image 20230912132941.png>)


### NoSQL DATABASES
> Non relational databases
> Benefits: Flexibility, Scalability, High-performance, Highly functional
> Example: Key-value, document, graph..

### Databases and Shared Responsibility on AWS
> AWS offers use to manage different databases
> Benefists include: 
> 	- Quick Provisioning: HA, Vertical and Horizontal Scaling
> 	- Automated Backup & Restore, Operations, Upgrades
> 	- OS Patching Handled by AWS(aws responsible)
> 	- Monitoring, Alerting
> Note: many databases tech could be run on EC2 but you must handle yourself the resiliency, backup, patching, HA, fault tolerance, scaling....

## AWS RDS
> RDS stands for Relational Database Service
> Its a managed DB service for DB use SQL as a query lang.
> It allows you to create databases in the cloud that are managed by AWS
>> Postgres
>> MySQL
>> MariaDB
>> Oracle
>> Microsoft SQL Server
>> Aurora(AWS Proprietary database)
>
>
### Advantage over using RDS vs deploying DB on EC2
> RDS is managed service:
>> Automate provisioning
>> Continuous backups and restore to spesific timestamp
>> Monitoring dashboards
>> Read replicas for improved read performance
>> Multi AZ setup for DR(disaster recovery)
>> Maintanence windows for upgrade
>> Scaling capability
>> Storage backed by EBS
> Note: CAN NOT SSH TO YOU DB
## RDS Solution Architecture
> ![image](<images/Pasted image 20230912134918.png>)
### Amazon Aurora
> Aurora is proprietary(tescilli) technology from AWS(not open sources).
> PostgreSQL and MySQL are both supported as Aurora DB
> Aurora is "AWS cloud optimized" and claims 5x performance improvement over Mysql, 3x 
over Postgres
> Aurora storage automatically grows in increments of 10GB, up to 128TB
> Aurora costs more than RDS(%20 more) - but is more efficient
> Not in the free tier

## RDS Deployments: Read Replicas, Multi-AZ
> Read Replicas:
>> Scale the read workload of your DB
>> Can create up to 15 read Replicas
>> Data is only written to the main DB
> Multi AZ:
>> Failover in case of AZ outage(HA)
>> Can only have 1 other AZ as failover
>> ![image](<images/Pasted image 20230912150904.png>)\
>Multi Region(Read replicas)
>>  Read Replicas across multi AZ
>>  Disaster recovery in case of region issue
>>  Local performance for global reads
>>  Replication costs up
>>  ![image](<images/Pasted image 20230912151042.png>)

## Amazon ElastiCache
> The same way RDS is to get managed Relational databases
> ElastiCache is to get managed Redis or Memcached
> Caches are in-memory dbs with high performance, low latency
> Helps reduce load of dbs for read intensive workloads
> AWS takes care of OS maintenance / patching, optimizations, setup, configuration, monitoring, failure recovery and backups
### ElastiCache Solution Architecture - Cache
> ![image](<images/Pasted image 20230912151613.png>)


## DynamoDB
> Fully managed HA with replication across 3 AZ 
> NoSQL database
> Scales to massive workload, distributed "serverless" database
> Million of requests per seconds, trillions of row 100s of TB of storage
> Fast and consistent in performance
> Single-digit ms latencty - low latency retrieval
> Integrated with IAM for security, auth and adminstration
> Low cost and auto scaling capabilities
> Standard  & Infrequent Access Table Class
### DynamoDB - type of data
> DynamoDB is a key/value database\
> ![image](<images/Pasted image 20230912152017.png>)

### DynamoDB Accelerator -DAX
> Fully managed in-memory cache for DynamoDB
> 10x performance improvement - single-digit milisecond lateny to microsecond latencty 
when accessing your DynamoDB tables
> Secure, HA & Highly scalable
> Difference with ElastiCache at the CCP level: DAX is only used for and is integrated with 
DynamoDB, while ElastiCache can be used for other databases\
> ![image](<images/Pasted image 20230912152350.png>)
### DynamoDB - Global Tables
> Make DynamoDB table accessible with low latency in multiple-regions
> Difference is write permission in every Zone
> Active-Active replication(read/write to any AWS region)\
> ![image](<images/Pasted image 20230912152849.png>)

### Redshift
> Based on PostreSQL but it is not used for OLTP(Online
Transaction Processing)
> Its OLAP - online analytical processing(analytics and data warehousing)
> Load data once every hour not every second
> 10x better performance than other data warehouses,
 scale to PBs of data
> Columnar storage of data(instead of row based)
> Massively parallel query execution(MPP), HA
> Pay as you go based on the instances provisioned
> Has a SQL interace for performing the queries
> BI(Business intelligence) tools such as AWS Quicksight
 or Tableu integrate with it

### Amazon EMR(Elastic MapReduce)
> EMR helps creating Hadoop clusters(Big data) to analyzeand process vast amount of data
> The clusters can be made of hundreds of EC2 instances
> Also supports Apache Spark, HBase, Presto, Flink..
> EMR takes care of all the provisioning and configuration
> Auto-scaling and integrated with Spot instances 
> Use cases:
		- Data processing
		- Machine learning
		- Web indexin
		- Big data
> Note: When you see Hadoop dont think it is EMR

### Athena
> Serverless query service to perfomr analytics against S3 
objects
> Uses standard SQL language to query the files
> Supports CSV, JSON, ORC, Avro and Parquet(build on 
Presto)\
> ![image](<images/Pasted image 20230912231952.png>)\
> Pricing: 5$ per TB of data scanned
> Use compressed or columnar data for cost-savings(less
scan) 
> Use cases: Business intelligence / analytics / reporting
analyze & query VPC Flow Logs, ELB Logs, CloudTrail
trails, etc..
> Note: Whenever you see analyze data in S3 using serverless SQL, use Athena

### Quicksight
> Serverless machine learning-powered business
intelligence service to ceate interactive dashboards
> Fast, automatically scalable, embeddable, with per-session pricing
> Allows you to create dashboard on your databases so
we can visually represent your data.
> Use Cases:
		- Business analytics
		- Building visualizations
		- Perform ad-hoc analysis
		- Get business insights using data
> Integrated with RDS, Aurora, Athena, Redshift, S3

### DocumentDB
> Aurora is an "AWS-implementation" of postgreSQL /
MySQL
> DocumentDB is the same for MongoDB(which is
NoSQL)
> MongoDB is used to store, query, and index JSON data
> Similar deployment concepts as Aurora
> Fully managed, HA with replication across 3 AZ
> DocumentDB storage automatically grows in
increments of 10GB, up 64Tb
> Automatically scales to workloads with milions of
requests per second.
> Note: Anythin related with mongoDB it is DocumentDB. Anythin related with NoSQL can be DocumentDb or
DynamoDB.

### Neptune
> Fully managed graph db
> A popular graph dataset would be a social network
> HA across 3 AZ, with up to 15 read replicas
> Build and run apps working with highly connected
datasets - optimized for these complex and hard queries
> Can store up to bilions of relations and query the graph with ms latency
> HA with replications across multiple AZs
> Great for knowlodge graph(Vikipedia), fraud detection, recommendation engines, social networking
> Note: Anythin related with the graph db it is Neptune

### QLDB(Quantum Ledger Database)
> A ledger is book recording financial transactions
> Fully managed, Serverless, HA,  Replication across 3 AZ
> Used to review history of all the changes made to your
app data over time. 
> Immutable system:  no entry can bbe removed or
modified, cryptographically verifiable.
>  2-3x better performance than commmon ledger
blockchain frameworks, manipulate data using SQL
> Note: Diff with Amazon Managed Blockchain: no decentralization component(that means there is just central db owned by Amazon that allows you to write journey), in accordance with financial regulation rules.
> Note: Anytime you see ledger or Financial transaction
think QLDB  

### Amazon Managed Blockchain
> Blockchain makes it possible to build apps where
multiple parties can execute transactions without the for a trusted, central authoiry,
> Amazon managed blockchain is a managed service to:
		- join public blockchain networks
		- Or create your own scalable private network
> Compatible with the frameworks HyperLedger Fabric &
Ethereum
> It is decentralized framework.
> Note: Anything related to Blockhains or Hyperledger Fabric or Ethereum think Amazon managed Blockchain.

### Glue
> Managed extract, transform, and load(ETL) service.
> Useful to prepare and transform data for analytics
> Fully serverless service\
>  ![image](<images/Pasted image 20230912234418.png>)

### DMS - Database Migration Service
> Quickly and securely migrate dbs to AWS, resilient, self
healing
> The source db remains available during the migration
> Supports:
> 	- Homogeneous migrations: ex Oracle to Oracle
> 	- Heterogeneous migrations: ex Microsoft SQL
> 	Server to Aurora
> Note: Whenever you see the migration of database DMS is the answer.

## SUMMARY
> Relational DB - OLTP(Online Transaction Processing) :
RDS & Aurora(SQL)
> Diff between Multi-AZ, Read Replicas, Multi-region
> In-memory db: ElastiCache
> Key/Value DB: DynamoDB(serverless) & DAX(cache for
DynamoDB)
> Warehouse - OLAP(Online analytical processing):
Redshift(SQL)
> Hadoop Cluster: EMR
> Athena: query data on S3(serverless & SQL)
> QuickSight: Dashboards on your data(serverless)
> DocumentDB: Aurora for MongoDB 
> Amazon QLDB: Financial Transactions Ledger
(immutable journal, cryptographically verifiable)
> Amazon Managed Blockchain: managed by
Hyperledger Fabric & Ethereum blockchains
> Glue: Managed ETL(Extract Transform Load) and Data
catalog service.
> Database migration: DMS
> Neptune: Graph database

