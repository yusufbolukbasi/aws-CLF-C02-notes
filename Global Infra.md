## CloudFront
> Content delivery platform
> Improves read performance, content is cached at the
edge.
> Improves users expreincec
> 216 Point Of Presence globally(Edge locations)
DDoS protection(because worldwide), integraion with
Shield, AWS Web App Firewall
### CludFront - Origins
> S3 bucket
>> For distributing files and cachind them at the edge
>> Enhanced security with CloudFron Origin Access
>Control(OAC).
>> CloudFron can be used as an ingress(to upload files to S3)
> Custom origin
>> Application Load Balancer
>> EC2 Instance
>> S3 website(must firs enable the bucket as a static S3 website)
>> Any HTTP backend you want.

### CloudFront at a high level
>![image](<images/Pasted image 20230918224156.png>)
### CloudFront - S3 as an Origin
>![image](<images/Pasted image 20230918224312.png>)

### CloudFront vs S3 Cross Region Replication
>CloudFront:
>> Global Edge Network
>> Files are cached for a TTL(maybe a day)
>> Great for static content that mus be available
>everywhere.
> S3 Cross Region Replication:
>> Must be setup for each region you want replication to
>happen.
>> Files are updated in near real-time
>> Read only
>> Great for dynamic content that needs to be available
>at low-latency in few regions.


## S3 Transfer Accelaration
> Increase transfer speed by transferring file to an AWS
Edge Location which will forward the data to the S3 bucket in the target region.
>![image](<images/Pasted image 20230918225611.png>)

## AWS Global Accelarator
> Improve global app availability and performance using
the AWS global network.
> Leverage the AWS internal network to optimize the route to your app. (60% improvement).\
> ![image](<images/Pasted image 20230918230103.png>)\
>![image](<images/Pasted image 20230918230144.png>)

### AWS Global Accelarator vs CloudFront
> They both use the AWS global network and its edge
locations around the world.
> Both services integrate with AWS Shield for DDoS
protection
> CloudFront - Content Delivery Network
>> Improves performance for you cacheable content (such as images and videos).
>> Content is served at the edge
> Global Accelarator
>> No cachng, proxying packets at the edge to apps
>running in one or more AWS regions.
>> Improves performance for a a wide range of apps
>over TCP and UDP
>> Good for HTTP use cases that require static IP
>addresses.
>> Good for HTTP use cases that required deterministic,
>fast regional failover.


## AWS Outposts
> AWS cloud infrastructure i on-prem kurulup datanin ve her seyin icerde tutulmasi.


## AWS Wavelength
> ![image](<images/Pasted image 20230918231507.png>)

## AWS Local Zones
> Places AWS compute storage, database, and other
selected AWS Services closer to end users to run latency-sensitive apps.
>  Extend you VPC to more locations - "Extension of an
AWS Region"
>  Compatible with EC2, RDS, ECS, EBS, ElastiCache, Direct
Connect

## Global Apps Architecture
> ![image](<images/Pasted image 20230918232041.png>)\
> ![image](<images/Pasted image 20230918232232.png>)


## SUMMARY
> Global DNS: Route 53
> Global Content Delivery(CDN): CloudFront
> S3 Transfer Acceleration
> AWS Global Accelarion
> AWS Outposts
> AWS WaveLength
> AWS Local Zones