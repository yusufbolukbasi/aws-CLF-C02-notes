## CDK(Cloud Development Kit)
> Define your cloud infra using familiar language: python
> The code is compiled into a CloudFormation template
> You can therefore deploy a infra and app runtime code
together
>> great for lambda funcs
>> great for docekr containers ECS/EKS\
> ![image](<images/Pasted image 20230914230514.png>)
### CDK Example
> ![image](<images/Pasted image 20230914230552.png>)

## Beanstalk
> Dev centric view of deploying an app on AWS
> It uses all components we have seen before
> One view thats easy to make sense of 
we still have full control over the conf
> <mark style="background: #FFB8EBA6;">Beanstalk == Platform as a Service(PaaS)</mark>
### Elastic Beanstalk
> Managed service
>> Instance conf / OS is handled by Beanstalk
>> Deployment strategy is configurable but performed
>by Elastic Beanstalk.
>> Capacity provisioning
>> Load Balancing & auto-scaling
>> Application health-monitoring & responsiveness
> Three architecture models:
>> Single instancse deployment: good for dev
>> LB + ASG: great for prod or pre-prod web apps
>> ASG only: Great for non-web apps in prod (workers..)
> Support for many platforms:
>> Programming languages
>> Docker

### Health monitoring
> Health agent pushes metrics to CloudWatch
> Checks for app health publishes health events

> Typical architecture : Web app 3-tier\
> ![image](<images/Pasted image 20230914230724.png>)
### Developer problems on AWS
> Managing infra
> Configuring all the dbs, load balancers
> Scaling concerns

## CODE
### CodeCommit
> Before pushing the app code to servers it needs to be
stored somewhere
> Dev usually store code in repo, using the Git technology
> A famous public offering is Github, AWS competing product is CodeCommit
> CodeCommit:
>> <mark style="background: #FFB8EBA6;">source-control service that hosts git-based repos</mark>
>> Git capabilities...
### CodeBuild
> <mark style="background: #FFB8EBA6;">Code building service</mark> in the cloud
> Compiles source code, run tests and produces packages that are ready to be deployed. 
> <mark style="background: #FFB8EBA6;">Serverless</mark>
> Pay as you go pricing - only pay for the build time\
>  ![image](<images/Pasted image 20230914233058.png>)

### CodePipeline
> Orchestrate the different steps to have the code automatically pushed to prod
>> Code > Build > Test > Provision > Deploy
>> Basis for CICD\
>>  ![image](<images/Pasted image 20230914233219.png>)\
> Benefits:
>> Fully managed, compatible with CodeCommit,
>CodeBuild, CodeDeploy, Elastic Beanstalk, CloudFormations, Github, 3rd-party Services & custom plugins
>> Fast delivery & rapid updated

### CodeArtifact
> Software packages depend on each other to be 
build(also called code dependencies) and new ones are created
> Storing and retrieving these dependencies is called
artifact management
> Traditionally you need to setup your own artiact
management system
> Works with common dependency management tools such as Maven, Gradle, npm, yarn, twine, pip and NuGet
> Devs and CodeBuild can then retrieve dependencies
straight from CodeArtifact

### CodeStar
> Unified UI to easily manage software development
activities in one place.
> Quick way to get started.
> Can edit the code "in-the-cloud" using AWS Cloud9

### Cloud9
> Cloud IDE for writing, running and debugging code.
> Classic IDE are downloaded on a computer before being used
> A cloud IDE can be used within a web browser meaning you can work on your projects from everywhere.
> AWS Cloud9 also allows code collabaration.


## AWS Systems Manager(SSM)
> Helps you manage your EC2 and on-prem systems at scale
> Another hybrid AWS service
> Get operational insights about the state of your infra
> Sutite of 10+ products
> Most important features are: 
>> Patching automation for enhanced compliance
>> Run commands across an entire fleet of servers
>> Stora parameter configuration with SSM Parameter Store
> Works for Linux, Windows, MacOS, and Raspberry OS

### How SSM Works
> ![image](<images/Pasted image 20230914235938.png>)

## SSM Session Manager
> Allows you to start a secure shell on you EC2 and on-prem servers
> No SSH Access, bastion hosts or SSH keys needed
> No port 22 needed
> Supports Linux, MacOS, Windows
> Send session log data to S3 or CloudWatch logs\
> ![image](<images/Pasted image 20230915000113.png>)

## OpsWorks
> Chef & Puppet help you perform server configuration automatically or repetitive actions
> They work great with EC2 & On-prem VM
> AWS OpsWorks = Managed Chef & Puppet
> Its an alternative to AWS SSM
> Only provision standard AWS resources:
>> EC2 instances, Dbs, load balancers,  EBS volumes
> In the exam: Chef or Puppet needed >> AWS OpsWorks

### OpsWorks Architecture
> ![image](<images/Pasted image 20230915000838.png>)

## SUMMARY
> CloudFormation
>> Infra as a Code, template
> Beanstalk 
>> Platform as a Service 
> CodeDeploy
> Systems Manager(hybrid)
> OpsWorks
