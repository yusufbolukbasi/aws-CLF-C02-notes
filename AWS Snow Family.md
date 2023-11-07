>Highly-secure portable devices to colet and process data at the edge and migrate data into and out of AWS
## Data migration: 
- Snowcone
- Snowball Edge
- Snowmobile
## Edge Computing
- Snowcone
- Snowball Edge

# Data migrations with aws Snow Family

### Aws Snow Family
>> Offline devices to perform data migrations
>> If it takes more than a week to transfer over the network, use Snowball devices

> Bildigin sana bir tane device veriyorlar icerisine datayi koyup device i shipliyorsan onlar sana import veya export edip donus yapiyor. 

### Snowball Edge(for data transfers)

![image](<images/Pasted image 20230910211442.png>)
### AWS Snowcone & Snowcone SSD
![image](<images/Pasted image 20230910211610.png>)
### AWS Snowmobile
![image](<images/Pasted image 20230910212111.png>)

## Snow Family - Usage Process
1. Request Snowball devices from the AWS console for delivery
2. Install snowball client
3. Connect the snowball to you servers and copy files using the client
4. Ship back the device when you are donw
5. Data will be loaded into and S3 bucket
6. Snowball is completely wiped


## What is edge computing?
>Process data while its being created on an edge location
>![image](<images/Pasted image 20230910212557.png>)

### Snow Family - Edge Computing
![image](<images/Pasted image 20230910212736.png>)

## AWS OpsHub
> Historically to use Snow Family devices you needed a CLI 
> Today, you can use AWS OpsHUB(a software you install on your computre) to manage your Snow Family Device

# Storage Gateway overview

## Hybrid Cloud for Storage
![image](<images/Pasted image 20230910213503.png>)
![image](<images/Pasted image 20230910213536.png>)
## AWS Storage Gateway
- Bridge between on-prem data and cloud data in S3
- Hybrid storage service to allow on-orem to seamlessly use the AWS Cloud
- Use cases: disaster recovery, backup & restore, tiered storage
- Types of storage Gateway
	- File Gateway
	- Volume Gateway
	- Tape Gateway
**No need to know the type at the exam**

# Amazon S3 - Summary
- Buckets vs Objects: global unique name, tied to a region 
- S3 Security: IAM Policy, S3 bucket policy, S3 Encryption
- S3 Website
- S3 versioning
- S3 replication
- S3 Storage Classes
- Snow Family
- OpsHub
- Storage Gateway

![image](<images/Pasted image 20230910214055.png>)



# SINAVA GIRMEDEN S3 IYI BIR TEKRAR EDILMELI


