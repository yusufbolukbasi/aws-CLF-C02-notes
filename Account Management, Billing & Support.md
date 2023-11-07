
## AWS Organizations
> Global service
> Allows to manage multiple AWS accounts
> Main account is called master account the other ones child account
> Cost Benefits:
> 	- **Consolidated Billing** across all accounts - single payment method
> 	- Pricing benefits from **aggregated usage** (volume discount for EC2, S3)
> 	- Pooling of **Reserved EC2 instances** for optimal savings
> API is available to automate AWS account creation
> **Restrict account privileges using Service Control Policies (SCP)**
> **THE BOLD ONES ARE EXAM**
### Multi Account Strategies
> Create accounts per **department**, per **cost center**, per **dev / test  / prod** based on 
**regulatory restrictions** (using SCP), for better **resource isolation** (ex: VPC), to have **separate per-account service limits**, **isolated account for logging**

> Multi account vs One account Multi VPC
> Use tagging standards for billing purposes
> Enable CloudTrail on all accounts, send logs to central S3 accounts
> Send CloudWatch Logs to central logging account
#### Organizational Units(OU) - Examples
>![image](<images/Pasted image 20231029113059.png>)
> ![image](<images/Pasted image 20231029113139.png>)

## Service Control Policies(SCP)
> Whitelist or Blacklist IAM actions
> Applied at the OU or Account level
> Does not apply to the Master Account
> SCP is applied to all the Users and Roles of the Account, including Root
> The SCP does not affect  service-linked roles
> 	- Service-linked roles enable other AWS services to integrate with AWS Organizations and cant be restricted by SCP's
> SCP must have an explicit allow (does not allow anything by default)
> Use cases:
> 	- Restrict access o certain services (for example: cant use EMR)
> 	- Enforce PCI compliance by explicitly disabling services
> ![image](<images/Pasted image 20231029114004.png>)
> ![image](<images/Pasted image 20231029114118.png>)

## Consolidated Billing
> When enabled, provides:
> 	- Combined Usage --> **Combine the usage** across all AWS accounts in the AWS Organization to **share the volume pricing**, **Reserved Instances and Saving Plans discounts**
> 	- One Bill --> get one bill for all AWS Accounts in the AWS Organizations \
> The management account can turn off Reserved Instances discount sharing for any
account in the AWS Organization, including itself.
> ![image](<images/Pasted image 20231029125738.png>)\
> In the exam you will be faced Shared volume pricing, shared volume discount, how to 
share what it means? 

## AWS Control Tower
> Easy way to set up and govern a secure and complian multi-account AWS Environment 
based on best practices.
> Benefis:
> 	- Automate the set up of your env in a few licks
> 	- Automate ongoing policy management using guardrails
> 	- Detect policy violations and remediate them
> 	- Monitor compliance through an interactive dashboard
>  AWS Control ower runs on top of AWS Organizations:
> 	 - It automatically sets up AWS organizations to organiza accounts and implement SCPs(Service Control Policies)

## AWS Resource Access Manager (AWS RAM)
> Share AWS resources that you own with other AWS accounts
> Share with any account or within your Organization
> Avoid resource duplication
> Supported resources include Aurora, VPC Subnets, Transit Gateway, Route 53, EC2 
Dedicated Hosts, Licence Manager Configurations\
> ![image](<images/Pasted image 20231029131600.png>)

## AWS Service Catalog
> Users that are new to AWS have too many options, and may create stacks that are not 
compliant / in line with the rest of the organization.
> Some users just want a quick self-service portal to launch a set of authorized product 
pre-defined by admins.
> Includes: vms, machines, dbs, storage options, etc..
![image](<images/Pasted image 20231029132423.png>)

## Pricing Model in AWS
> AWS has 4 pricing models
> 	- Pay as you go --> pay for what you use, remain agile, responsive, meet scale demands
> 	- Save when you reserve --> minimize risks, predictably manage budgets, comply with long-terms requirements
> 		- Reservations are available for EC2 Reserved Instances, DynamoDB Reserved Capacity, ElastiCache Reserved Nodes, RDS Reserved Instance, Redshift Reserved Nodes
> 	- Pay less by using more --> Volume-based discounts
> 	- Pay less as AWS grows
### Free services & Free tier in AS
> - IAM, VPC, Consolidated Billing
> - Elastic Beanstalk, CloudFormation, Auto Scaling Groupst --> You do pay for the 
> resource created

### Compute Pricing - EC2
> Only charged for what you use
> Number of instances
> Instance configuration
> 	- Physical capacity
> 	- Region
> 	- OS and Software
> 	- Instance type
> 	- Instance size
> ELB running time and amount of data processed
> Detailed monitoring
> Different models of pricing - EC2:
> 	- On-demand Instances --> 
> 		- Minimum billing time 60s
> 		- Pay per second (Linux/Windows) or per hour (other)
> 	- Reserved Instances:
> 		- Up to %75 discount compared to On-demand hourly rate
> 		- 1 or 3 years commitment
> 		- All upfront, partial upfront, no upfront(on odeme)
> 	- Spot Instances:
> 		- Up to %90 discount compared to On-demand on hourly rate
> 		- Bid for unused capacity
> 	- Dedicated Host:
> 		- On-demand
> 		- Reservation for 1 year or 3 years commitment
> 	- Saving plans
> 		- as an alternative to save on sustained usage

### Compute Pricing - Lambda & ECS
> - Lambda 
> 	- Pay per call
> 	- Pay per duration
> - ECS
> 	- EC2 Launch Type Model: No additional fees, you pay for AWS resources stored and created in your app
> - Fargate
> 	- Fargate Launch Type Model: Pay for vCPU and memory resources allocated to you apps in your containers

### Storage Pricing - S3
> Storage Class --> Standard, Infrequent Access, One-Zone IA, Intelligent Tiering, Glacier, 
Glacier Deep Archive
> Number and size of objects: Price can be tiered (based on volume)
> Number adn type of requests
> Data transfer out of the S3 region
> S3 Transfer Acceleration
> Lifecycle transitions

> Similar Service: EFS (pay per use, has infrequent access & lifecycle rules)

### Storage Pricing - EBS
> Volume type (based on performance)
> Storage volume in GB per month provisionned
> IOPS: --> Performance of the volume
> 	- General Purpose SSD: Included  the default price
> 	- Provisioned IOPS SSD: Provisionned amiunt in IOPS
> 	-  Magnetic: Number of requests
> Snaphots --> data cost per GB per month
> Data Transfer
> 	- Outbound data transfer are tiered for volume discounts
> 	- Inbount is free

### Database Pricing - RDS
> Per hour billing
> Database characacteristics
> 	- Engine
> 	- Size
> 	- Memory class
> Purchase type
> 	- On-demand
> 	- Reserved Instances(1-3 years) with required up-front
> Backup Storage --> there is no additional charge for backup storage up to %100 of your 
total database storage for a region
> Additional storage (per GB per month)
> Number of input and output requests per month
> Deployment type (storage and I/O are variable)
> 	- Single AZ
> 	- Multi AZ
> Data transfer
> 	- Outbound data transfer are tiered for volume discounts
> 	- Inbound is free

### Content Delivery - CloudFront
> Pricing is different across different geographic regions
> Aggregated for each edge location, then applied to your bill
> Data Transfer Out(volume discount)
> Number of HTTP/HTTPS requests
> ![image](<images/Pasted image 20231029135318.png>)

### Networking Costs in AWS per GB - Simplified
> Use private IP insteod of Public for good savings and better network performance
> Use same AZ for maximum savings (at the cost of high availability)
![image](<images/Pasted image 20231029135709.png>)

## Savings Plan 
>  Commit a certain $ amount per hour for 1 or 3 years
>  Easiest way to setup long-term commitments on AWS
>  The are 3 types of saving plans
> 	 - EC2 Saving Plan
> 		 - Up to %72 discount compated to On-Demand
> 		 - Commit to usage of individual instance families in a region(e.g. C5 or M5)
> 		 - Regardless of AZ, size (m5.xl to m5.4xl), OS(Linux/Windows) or tenancy
> 		 - All upfront, partial upfront, no upfront
> 	 - Compute Saving Plan
> 		 - Up to %66 discount compated to On-demand
> 		 - Regardless of Family, Region, size OS tenancy, compute options --> EC2, Fargate, Lambda
> 	 - Machine Learning Savings Plan: SageMaker
>  Setup from the AWS Cost Explorer console

## AWS Compute Optimizer
> Reduce costs and improve performance by recommending optimal AWS resources for your workloads
> Helps you choose optimal configurations and right size you workloads (over/under provisioned)
> Uses ML to analyze your resources configurations and their utilization CloudWatch metrics
> Supported resources
> 	- EC2 instances
> 	- EC2 Auto Scaling Groups
> 	- EBS volumes
> 	- Lambda funcs
> Lower your costs by up to %25
> Recommendations can be exported to S3\
> ![image](<images/Pasted image 20231029142149.png>)

## Billing and Costing Tools
### Estimating costs in the cloud
> Pricing calculator
### Tracking costs in the cloud
> Billing dashboard
> Cost Allocation Tags
> Cost and Usage Reports
> Cost explorer

### Monitoring against costs plans
> Billing alarms
> Budgets

## AWS Pricing Calculator
> Estimate the cost of your solution architecture\
> ![image](<images/Pasted image 20231029142339.png>)

## AWS Billing Dashboard
> ![image](<images/Pasted image 20231029142614.png>)

## AWS Free Tier Dashboard
> ![image](<images/Pasted image 20231029142641.png>)

## Cost Allocation Tags
> Use cost allocation tags to track your AWS costs on a detailed level
> AWS generated tags
> 	- Automatically applied to the resource you create
> 	- Starts with prefix aws:
> User defined tags
> 	- Defined by the user
> 	- Starts with prefix user:
## Tagging and Resource Groups
> Tags are used for organizing resources
> Free naming, common tags are Name, Env, Team
> Tags can be used to create Resource Groups
> 	- Create, maintain and view a collection of resources that share common tags
> 	- Manage these tags using the Tag Editor

## Cost and Usage Reports
> Dive deeper into your AWS costs and usage
> The AWS cost and Usage report contains the most comprehensive set of AWS cost and 
usage data available, including additional metadata about AWS services, pricing and reservations.
> The AWS cost and Usage Report lists AWS usage for each service category used by an 
account and its IAM users in hourly or daily line items as well as any tags that you have activated for cost allocation purposes.
> Can be integrated with Athena, Redshift or Quicksight\
> ![image](<images/Pasted image 20231029143556.png>)

## Cost Explorer
> Visualize, understand and manage your AWS costs and usage over time
> Create custom reports that analyze cost and usage data
> Analyze your data at a high level: total costs and usage across all accounts
> Or monthly, hourly resource level granularity
> Choose and optimal Savings Plan (to lower prices on your bill)
> **Forecast usage up to 12 months based on previous stage** --> **EXAM QUESTION**
> ![image](<images/Pasted image 20231029143808.png>)
> ![image](<images/Pasted image 20231029143835.png>)![image](<images/Pasted image 20231029143855.png>)
> ![image](<images/Pasted image 20231029143915.png>)

## Billing Alarms in CloudWatch
> Billing data metric is stored in CloudWatch us-east-1
> Billing data are for overall worldwide AWS costs
> Its for actual cost, not for projected costs
> Intended a simple alarm (not as powerful as AWS Budgets)

## AWS Budgets
> Create budget and send alarms when costs exceeds the budget
> 4 types of budgets: Usage, Cost, Reservation, Saving Plans
> For Reserved Instances (RI)
> 	- Track utilization
> 	- Supports EC2, ElastiCache, RDS, Redshift
> Up to 5 SNS notifications per budget
> Can filter by: Service, Linked Account, Tag, Purchase Option, Instance Type, Region, AZ, API
Operation, ...
> 2 budgets are free, then 0,02$/day/budget

## AWS Cost Anomaly Detection
> Continuosly monitor your cost and usage using ML to detect unusual spends
> It learns your unique, historic spend patterns to detect one-time cost spike and/or continuous cost
increases. (you dont need to define thresholds)
> Monitor AWS services, member accounts, cost allocations tags, or cost categories
> Send you the anomaly detection report with root-cause analysis
> Get notified with individual alerts or daily/weekly summary (using SNS --> mail)\
> ![image](<images/Pasted image 20231031175547.png>)

## AWS Service Quotas
> Notify you when you are close to a service quota value threshold
> Create CloudWatch Alarms on the Service Quotas console
> Example: Lambda concurrent executions
> Request a quota increase from AWS Service Quotas or shutdown resources before limit is reached.\
> ![image](<images/Pasted image 20231031210201.png>)

## Trusted Advisor
> No need to install anything - high level AWS account assessment.
> Analyze your AWS accounts and provides recommendation on **5 categories** --> **IMPORTANT**
> 	 - Cost optimization
> 	 - Performance
> 	 - Security
> 	 - Fault Tolerance
> 	 - Service limits\
>  ![image](<images/Pasted image 20231031210516.png>)
### **WHAT ARE SOME OF THE CORE CHECKS OF TRUSTED ADVISOR?** --> CAN BE EXAM QUESTION
#### 7 core checks --> Basic and Developer Support Plan
>  - S3 bucket Permissions
>  - Security Groups - Spesific Ports Unrestricted
>  - IAM use (one IAM user minimum)
>  - MFA on Root Account
>  - EBS Public Snapshots
>  - RDS Public Snapshots
>  - Service Limits
#### Full Checks --> Business & Enterprise Support Plan
>	- Full checks available on the 5 categories
>	- Ability to set CloudWatch alarms when reaching limits
>	- Programmatic Access Using AWS Support API

## AWS Support Plans Pricing
> Basic Support: Free\
> ![image](<images/Pasted image 20231031211334.png>)

### AWS Basic Support Plan
> Customer Service & Communities -  7x24 access to customer service, documentation, whitepapers, 
and support forums.
> AWS Trusted Advisors - Access to the 7 core Trusted Advisor checks and guidance to provision your 
resources following best practices to increase performance and improve security.
> AWS Personal Health Dashboard - A personalized view of the health of AWS services, and alerts 
when your resources are impacted

### AWS Developer Support Plan
> All Basic Support Plan 
> Business hours email access to Cloud Support Associates
> Unlimated cases / 1 primary contact
> Case severity / response times:
> 	- General guidance < 24 business hours
> 	- System impaired < 12 business hours

### AWS Business Support Plan (7/24)
> Intended to be used if you have production workloads
> Trusted Advisor - Full set of checks + API access
> 7x24 phone, email, and chat access to Cloud Support Engineers
> Unlimited cases / unlimited contacts
> Access to infra Event management for additional fee
> Case severity / response times
> 	- General Guidance: < 24 business hours 
> 	- System impaired: < 12 business hours
> 	- Prod system impaired: < 4 hours
> 	- Prod system down: < 1 hour

### AWS Enterprise On-Ramp Support Plan
> Intented to be used if you have prod or business critical workloads
> All of Business Support plan +
> Access to pool of Technical Account Managers (TAM)
> Concierge Support Team (for billing and account best practices)
> Infrastructure Event Management, Well-Architected & Operations Reviews
> Case severity / response times:
> 	- ...
> 	- Prod system impaired: < 4 hours
> 	- Prod system down: < 1 hour
> 	- Business-critical system down: < 30 minutes

AWS Enterprise Support Plan (7/24)
> Intended to be used if you have mission critical workloads
> All of business support plan + 
> Access to designated Technical Account Manager(TAM)
> Concierge Support Team (for billing and account best practices)
> Infrastructure Event Management, Well-Architected & Operations Reviews
> Case severity / response times:
> 	- ...
> 	- Prod system impaired: < 4 hours
> 	- Prod system down: < 1 hour
> 	- Business-critical system down: < 15 minutes

## ACCOUNT BEST PRACTICES - SUMMARY
> Operate multiple accounts --> **AWS Organizations**
> Use **SCP** (service control policies) to restrict account power 
> Easily setup multiple accounts with best-practices with **AWS Control Tower**
> **Use Tags & Cost Allocation Tags**for easy management & billing
>**IAM Guidelines**: MFA, least-privilege, password policy, password rotation
> **AWS Config** to record all resources configurations & compliance over time
> **CloudFormation** to deploy stacks across accounts and regions
>**Trusted Adviso**r to get insights, Support Plan adapted to your needs
> Send service logs and Access logs to **S3 or CloudWatch Logs**
> **CloudTrail** to record API calls made within you account
> **If your Account is compromised**: change the root password, delete and rotate all passwords / keys, 
contact the AWS Support
> Allow users to create pre-defined stacks defined by admins using **AWS Service Catalog**

## BILLING AND COSTING TOOLS - SUMMARY
> Compute Optimized: recommends resources configurations to reduce cost - uses ML
> Pricing Calculator: calculate the cost of services on AWS
> Billing Dashboard: high level overview + free tier dashboard
> Cost Allocation tags: tag resources to create detailed reports
> Cost and Usage Reports: most comprehensive billing dataset
> Cost Explorer: View current usage (detailed) and forecast usage
> Billing Alarms: in us-east-1 - track overall and per-service billing
> Budgets: More advance - track usage, costs, RI, and get alerts
> Saving Plans: Easy way to save based on long-term usage of AWS
> Cost Anomaly Detection: detect unusual spends using ML
> Service Quotas: Notify you when you are close to service quota threshold.
