## AWS Shared Responsibility Model

### AWS responsibility - Security of the Cloud
> Protecting infra (hardware, software, facilities, and networking) that runs all the AWS 
services
> Managed services like S3, DynamoDB, RDS, etc..
### Customer Responsibility - Security in the Cloud
> For EC2 instance. customer is responsible for management of the guest OS, firewall & 
network configs, IAM
> Encrypting app data
### Shared Controls
> Patch management, Configuration management, Awareness & Training

#### Example of RDS
##### AWS Responsibility
> Manage the underlying EC2 instance, disable SSH access
> Automated DB patching
> Automated OS patching
> Audit the underlying instance and disks & guarentee it functions
##### Your responsibility
> Check the ports / IP / Security group inbound rules in DB's SG
> In-database user creation and permissions
> Creating a database with or without public access
> Ensure parameter groups or DB is configured to only allow SSL connections.
> Database encryption setting

![image](<images/Pasted image 20231028114135.png>)

## DDOS Attack
> 	- AWS Shield Standard: protects against DDOS attack for your website and apps, for all customers at no additional costs
> 	- AWS Shield Advanced: 7/24 premium DDOS protection
> 	- AWS WAF: Filter spesific requests based on rules
> 	- CloudFront and Route53:
> 		- Availability protection using global edge network.
> 		- Combined with AWS Shield, provides attack mitigation at the edge
> 	- Be ready to scale - leverage **AWS Auto Scaling**\
![image](<images/Pasted image 20231028114648.png>)

## AWS Shield
### AWS Shield Standard
> 	- Free
> 	- Provides protection from attacks such as SYN/UDP Floods, Reflection attacks and layer 3 and layer 4 attacks
### AWS Shield Advanced
> 	- Optional DDoS mitigation service(3000$ per month per organization)
> 	- Protect against more sophisticated attack on EC2, ELB, CLoudFront, Global Accelarator and Route 53
> 	- 7/24 Access to AWS DDoS response team
> 	- Protect against higher fees during usage spikes due to DDoS

## AWS WAF - web app firewall
> Protects you web apps from common web exploits (Layer 7)
> Layer 7 is HTTP (vs layer 4 is TCP)
> Deploy on Application Load Balancer, API Gateawy CloudFront
> Define Web ACL (Web Access Control List):
> 	- Rules can include IP addresses, HTTP headers, HTTP body, or URI strings
> 	- Protects from common attack - SQL Injection and Cross-Site Scripting
> 	- Rate-based rules - for DDoSS protection

## AWS Network Firewall
> Protect your entire Amazon VPC
> From layer 3 to layer 7 direction
> Any direction you can inspect
> 	- VPC to VPC traffic
> 	- Outbound to internet
> 	- Inbound from Internet
> 	- To/From direct connect & Site to Site VPN 

## Penetration Testing on AWS Cloud
> AWS customers are welcome to carry out security assesments or penetration tests 
against their AWS infra without prior approval for 8 services
> 	- EC2 instances, NAT Gateways, and Elastic Load Balancers
> 	- Amazon RDS
> 	- CloudFront
> 	- Aurora
> 	- API Gateways
> 	- Lambda and Lambda Edge Functions
> 	- Lightsail Resources
> 	- Elastic Beanstalk Envs
> List can increase over time
> Prohibited Activities
> 	- DNS zone walking via Amazon Route 53 Hosted Zones
> 	- Denial Of Service(DoS), DDoS, Simulated DoS, Simulated DDoS
> 	- Port flooding
> 	- Protocol flooding
> 	- Request flooding (login request flooding, API request flooding)

## Encryption with KMS and CloudHSM
> There is two type of encryption method
> 	- At rest: data stored or archived on a device
> 		- On a hard disk, on a RDS instance, in S3 Glacier Deep Archive
>	- In transit (in motion): data being moved from one location to another
>		- Transfer from on-prem to AWS, EC2 to DynamoDB, etc.
>		- Means data transferred on the network
> We want to encrypt data in both states to protect it. For this we leverage encryption keys.

## AWS KMS (Key Management Service)
> Anytime you hear "encryption" for an AWS service its most likely KMS
> KMS = AWs manages the encryption keys for us
> Encryption optional for theese services:
> 	- EBS volumes --> encrypt volumes
> 	- S3 buckets --> Server-side encryption of objects
> 	- Redshift database --> encrypts data
> 	- RDS database --> encrypts data
> 	- EFS drives --> encrypts data
> 	Encryption Automatically enables:
> 		- CloudTrail Logs
> 		- S3 Glacier
> 		- Storage Gateway

### CloudHSM
>  KMS --> AWS manages the software for encryption
>  CloudHSM --> AWS provisions encryption **hardware**
>  Dedicated Hardware (HSM = Hardware Security Module)
>  You manage your own encryption key entirely (not AWS)\
>  ![image](<images/Pasted image 20231028121006.png>)

## Types of Customer Master Keys: CMK
### Customer Managed CMK:
> Create, manage and used by the customer, can enable or disable
> Possibility of rotation policy (new key generated every year, old key preserved)
> Possibility to bring-your-own-key
### AWS Managed CMK:
> Created, managed and used on the customers's behalf by AWS
> Used by AWS services

### AWS owned CMK:
> Colection CMKs that an AWS service owns and manages to use in multiple accounts
> AWS can use those to protect resources in your account (but you can not view the keys)

### CloudHSM Keys (custom keystrote)
> Keys generated from your own CloudHSM hardware device
> Cryptographic operations are performed within the CloudHSM cluster

## AWS Certificate Manager(ACM)
> Easily provision, manage and deploy SSL/TLS Certificates
> Used to provide in flight encryption for websites (HTTPS)
> Supports both public and private TLS certificates
> Free of charge for public TLS certificates
> Automatic TLS certificate renewal
> Integrations with (load TLS certificates on)
> 	- Elastic Load Balancers
> 	- CLoudFront Distributions
> 	- APIs on API Gateway

## Secrets Manager
> Newer service meant for storing secrets
> Capability to force rotation of secrets every X days
> Automate generation of secrets on rotations (uses Lambda)
> Integration with Amazon RDS (MySQL, PostgreSQL, Aurora)
> Secrets are encrypted using KMS
> Mostly meant for RDS integration.
> **ANYTIME YOU SEE SECRET TO BE MANAGING IN RDS YOU SHOULD REMEMBER SECRETS MANAGER**

## Artifact (not really a service)
> Portal that provides customers with on-demand access to AWS compliance reports and AWS agreements
> 	- Artifact Reports - Allows you to download AWS security and compliance documents from third-party auditors, like AWS ISO certifications, Payment Card Industry(PCI), and System and Organization Control(SOC) reports.
> 	- Artifact agreements - Allows you to review, accept, and track the status of AWS agreements such as the Business Associate Addendum(BAA) or the Health Insurence Portability and Accountability Act(HIPAA) for an individual account or in your organization
> Can be used to support internal audit or compliance

## GuardDuty
>  Intelligent Threat discovery to protect your AWS Account
>  Uses ML algorithms, anomaly detection 3rd party data
>  One click to enable (30 days trial), no need to install software
>  Input data includes:
> 	 - CloudTrail Events Logs: unusual API calls, unauthorized deployments
> 		 - CloudTrail Management Events - create VPC subnet, create trail
> 		 - CloudTrail S3 Data Events - get object list, delete object
> 	 - VPC Flow Logs - unusual internal traffic, unusual IP address
> 	 - DNS logs - compromised(riske atılmış) EC2 instances sending encoded data within DNS queries.
> 	 - Optional features - EKS Audit Logs, RDS & Aurora, EBS, Lambda, S# Data Events
>  Can setup EventBridge rules to be notified in case of findings.
>  EventBridge rules can target AWS Lambda or SNS
>  Can protect against CryptoCurrency attacks (has a dedicated 'finding' for it)\
>  ![image](<images/Pasted image 20231028133425.png>)

## Inspector
> Automated Security Assessments
> For EC2 instances
> 	- Leveraging the AWS System Manager(SSM) agent
> 	- Analyze against unintended network accessibility
> 	- Analyze the running OS against known vulnerabilities.
> For Container Images push to Amazon EC2
> 	- Assessment of container images as they are pushed
> For Lambda Funcs
> 	- Indentifies software vulnerabilities in fucntion code and package dependencies
> Reporting and Integration with AWS Security Hub
> Send findings to Amazon Event Bridge
### What does Amazon Inspecter evaluate?
> Remember: only for EC2 instannces, Contaner Images and Lambda funcs
> Continuous scanning of the infra, only when needed
> Package vulnerabilities (EC2, ECR and Lamba) - database of CVE
> Network Reachability(EC2)
> A risk score is associated with all vulnerabilities for prioritization

## AWS Config
> Helps with auditing and recording compliance of your AWS resources
> Helps record configurations and changes over time
> Possibility of storing the conf data into S3 (analyzed by Athena)
> Questions that can be solverd by AWS Config:
> 	- Is there unrestricted SSH access to my security group
> 	- Do my buckets have any public access 
> 	- How has my ALB configuration changed over time?
> You can receive alerts (SNS notification) for any changes
> AWS Config is a per-region service
> Can be aggregated(birleştirmek) across regions and accounts
### Config Resource
> View compliance of a resource over time\
> ![image](<images/Pasted image 20231028135546.png>)\
> View configuration of a resource over time\
> ![image](<images/Pasted image 20231028135556.png>)\
> View CloudTrail API calls if enabled

## Macie
> Fully managed data security and data privacy service that uses ML and pattern matching 
to discover and protect you sensitive data in AWS.
> Macie helps identify and alert you to sensitive data, such as personally identifiable 
information(PII)\
> ![image](<images/Pasted image 20231028140813.png>)

## Security Hub
> Central Security tool to manage security across several AWS accounts and automate 
security checks
> Integrated dashboards  showing current security and compliance status to quickly take 
actions.
> Automatically aggregates alerts in predefined or personal findings formats from various AWS services and AWS partner tools
> 	- Config
> 	- GuardDuty
> 	- Inspector
> 	- Macie
> 	- IAM Access Analyzer
> 	- AWS Systems Manager
> 	- AWS Firewall Manager
> 	- AWS Health
> 	- AWS Partner Network Solutions
> Must first enable the AWS Config Service\
> ![image](<images/Pasted image 20231028141448.png>)

## Amazon Detective
> GuardDuty, Macie and Security Hub are used to identify potential security issues or 
findings.
> Sometimes security findings require deeper analysis to isolate the root cause and take 
action - it's a complex process
> Amazon Detective analyzes, investigates and quickly identifies the root cause of security 
issues or suspicious activities(using ML and graphs)
> Automatically collects and processes events from VPC Flow Logs, CloudTrail, GuardDuty 
and create a unified view. 
> Produces visualizations with details and context to get to the root cause.

## AWS Abuse
>![image](<images/Pasted image 20231028142310.png>)

## Root User Privileges
> Root use = Account Owner
> Has complete access to all AWS services and resources
> Lock away your AWS account root user access keys
> Do not use the root account for everyday tasks event administrative tasks
> Actions that can be performed only by the root user
> 	- C**hange account settings** (account name, email address, root user password-access 
> 	keys)
> 	- View certain tax invoices.
> 	- **Close your AWS account**
> 	- Restore IAM user permissions
> 	- **Change or cancel your AWS Support plan**
> 	- **Register as a seller in the Reserved Instance Marketplace**
> 	- Configure an Amazon S3 bucket to enable MFA
> 	- Edit or delete an Amazon S3 buckete policy that includes an invalid VPC ID or VPC endpoint ID
> 	- Sign up for GovCloud
> **THE BOLD ONES ARE IMPORTANT CAN BE FACED IN THE EXAM**

## IAM Access Analyzer
> Find out which resources are shared externally
> 	- S3 buckets
> 	- IAM Roles
> 	- KMS Keys
> 	- Lambda funcs and layers
> 	- SQS queues
> 	- Secrets Manager Secrets
> Define **ZoneofTrue**= AWS Account or AWS Organization
> Access outside zone of trusts --> Findings.\
> ![image](<images/Pasted image 20231028143650.png>)

## SUMMARY
> Shaed responsibility on AWS
> Shield --> Automatic DDoS protection
> WAF --> Firewall to other incoming requests based on rules
> KMS --> encryption keys managed by AWS
> CloudHSM --> Hardware encryption, we manage encryption keys
> AWS Certificate Manager(ACM) --> provision, manage and deploy TLS/SSL certificates
> Artifact --> Get access to compliance reports such as PCI, ISO, etc..
> GuardDuty --> Find malicious behavior with VPC, DNS and CloudTrail Logs
> Inspector --> find software vulnerabilities in EC2, ECR Images and Lambda funcs
> Network Firewall --> Protect VPC against network attacks
> Config --> Track config changes and compliance against rules
> Macie --> Find sensitive data in Amazon S3 buckets
> CloudTrail --> Track API calls amde by users within account
> AWS Security Hub --> gather security findings from multiple AWS accounts
> Amazon Detective --> find the root cause of security issues or suspicious activities
> AWS Abuse --> Report AWS resources used for abusive or illegal purposes
> Root user privileges:
> 	- Change account settings
> 	- Close your AWS account
> 	- Change or cancel your AWS support plan
> 	- Register as a seller in the Reserved Instance Marketplace
