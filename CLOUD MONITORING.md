## CloudWatch
### CloudWatch Metrics
> provides metrics for every services in AWS
> Metric is variable to monitor(CPUUtilization, NetworkIn)
> Metrics have timestamps
> Can create CloudWatch dashboards of metrics\
>  ![image](<images/Pasted image 20230919223810.png>)
#### Important Metrics
> EC2 Instances: CPU utilization, Status check,
Network(not RAM)
>> Default metrics every 5 minutes
>> Option f or detailed monitoring("paraaa"): metrics every 1 minute
> EBS Volumes: Disk Read/Writes
> S3 Buckets: BucketSizeBytes, NumberOfObjects,
AllRequests
> Billing: Total Estimated Charge(only in us-east-1)
> Custom Metrics: push your own metrics

### CloudWatch Alarms
> Alarms are used to trigger notification for any metric
> Alarms actions:
>> Auto scaling:
>> EC2 Actions:
>> SNS notifications
> Various Options( sampling, %, max, min)
> Can choose the period on which to evaulate an alarm
> Example: create a billing alarm on the CloudWatch
Billing metric
> Alarm States: OK, INSUFFICIENT DATA, ALARM

### CloudWatch Logs
> Can collect log from Elastic Beanstalk --> from app, ECS(Elastic Container service) --> from containers, Aws Lambda -->
collection from function, CloudTrail --> based on filter, CloudWatch log agents --> EC2 machines or on-prem servers,
Route53 --> Log DNS queries.
> Enables real-time monitoring of logs
> Adjustable CloudWatch Logs retention
#### How does CloudWatch logs work for EC2 Instances
> By default no logs from your EC2 instance will go to CloudWatch.
> You need to run a CLoudWatch agent on EC2 to push the log files you want.
> Make sure IAM permissions are correct
> The CloudWatch log agent can be setup on-prem too.

### EventBridge (CloudWatch Events)
> Schedule: Cron jobs
> Event pattern: Event rules to react to a service doing something.
>> For example: If IAM root User Sign in Event Then > SNS(Simple Notification Service) topic with email notification.\
> ![image](<images/Pasted image 20231014201703.png>)

#### EventBridge Capability
>![image](<images/Pasted image 20231014201815.png>)\
>Scheme Registry: model event schema
>You can archive events sent to an event bus(indefinetly or set period)
>Ability to replay archived events.

### CloudTrail
> Provides governance, compliance and audit for your AWS account
> It is enabled by default
> Get an history of events / API calls made within you AWS account.
> 	- Console
> 	- SDK
> 	- CLI
> 	- AWS Services
> Can put logs from CLoudTrail into CloudWatch Logs or S3
> A  trail can be applied to All Regions(default) or a Single Region
> If a resource is deleted in AWS, investigate CloudTrail first.\
> ![image](<images/Pasted image 20231015153703.png>)

### X-Ray
> Debugging in Prod, the good old way
>  - Test Locally
>  - Add log statements evertwhere
>  - Re-deploy in prod
> Problems: 
> 	- Log formats differ across apps and log analysis is hard
> 	- Debugging: one big monolith "easy", distrubuted services "hard"
> 	- No common views of your entire architecture
> X - ray is the solution of the problems.
> X - ray provides visual analysis of out apps.
#### Advantages of X-ray
> Troubleshooting performence (bottlenecks)
> Understand dependencies in a microservice architecture
> Pinpoint service issues
> Reviewe request behavior
> Find errors and exceptions
> Are we meeting time SLA(Service level agreement)
> Where  I am throttled?
> Identify users that are impacted

### CodeGuru
> ML-powered service for automated code reviews and app performance recommendations
> Provides two functionalities:
> 	- CodeGuru Reviewer: automated code reviews for static code analysis (development)
> 	- CodeGuru Profiler: Visibility/recommendations about app performance during runtime (production)

### Health Dashboard
#### Service history
> Show all regions, all aws services health
> Shows historical info for each day
> Has an RSS feed you can subscribe to
> Previously called AWS Service Health Dashboard

#### Your Account
> Called AWS Personal Health Dashboard
> Service history for you account.
> Provides proactive notification
> Can aggregate data from an entire AWS Organization

### SUMMARY
> CloudWatch
> 	- Metrics monitor performance of services and billing metrices
> 	- Alarms: automate notification, perform EC2 action, notify to SNS based on metric
> 	- Logs: collect log files from EC2 instances, servers, Lambda functions
> 	- Events( or EventBridge): react to events in AWS, or trigger a rule on a schedule
> CloudTrail
> 	- Audit API calls within your AWS account
> CloudTrail Insights
> 	- automated analysis of your CloudTrail Events
> X-Ray
> 	- trace requests made through your distributed apps
> AWS Health Dashboard
> 	- status of all AWS services across all regions
> AWS Account Health Dashboard
> 	- AWS Events that impact your infra
> CodeGuru
> 	- automated code reviews and app performance reccomedations
>  