### VPC (Virtual Private Cloud)
> ![image](<images/Pasted image 20231020170124.png>)

### IP Addresses in AWS
> Public IPv4 --> can be used on the internet
> EC2 instance gets a new a public IP address every time you restart.
> Private IPv4 --> can be used on private networks(LAN) such as internal AWS networking
> Private IPv4 is fixed for EC2 instances even if you start/stop them.

### Elastic IP (cost)
> allows you to atach a fixed public IPv4 address to EC2 instance. 
> 	- Note: Has ongoing cost if not attached to EC2 instance or if the EC2 instance is stopped

### IPv6

## VPC & Subnets Primer
> **VPC - Virtual Private Cloud:** private network to deploy your resources(regional resource)
> **Subnets** Allow you to partition your network inside you VPC (AZ resource)
> A public subnet is a subnet that is accessible from the internet
> A private subnet is a subnet that is not accessible from the internet
> To define access to the internet and between subnets, we use Route Tables. 
### VPC Diagram

> ![image](<images/Pasted image 20231027162948.png>)

### Internet Gateway & NAT Gateways 
> Internet Gateways
> 	- Helps our VPC instances connect with the internet
> 	- Public Subnets have a route to the internet gateway
> Nat Gateways(AWS Manaeged) & Nat Instances(Self managed)
> 	- Allow your instances in your **Private Subnets** to access the internet while remaining private\
> 	- ![image](<images/Pasted image 20231027163335.png>)

## Network ACL & Security Groups 

### NACL (Network Access Control List) --> SUBNET LEVEL NETWORK RULES
> A firewall which controls traffic from and to subnet
> Can have ALLOW and DENY rules
> Are attached at the Subnet level
> Rules only include IP  addresses
### Security Groups --> INSTANCE LEVEL NETWORK RULES
> A firewall that controls traffic to and from an ENI(Elastic Network Interface)/ and EC2 instance
> Can have only ALLOW rules
> Rules include IP addresses and other security groups.\
> ![image](<images/Pasted image 20231027164714.png>)


| Security Groups | Network ACL |    
| :---:   | :---: |
| Operates at the instance levels | Operates at the subnet level |
| Supports allow rules only | Supports allow rules and deny rules
| Is stateful: Return traffic is automatically allowed, regardless of any rules | Is stateless Return traffic must be explicitly allowed by rules |
| We evaluate all rules before deciding whether to allow traffic | We process rules in number order when deciding whether to allow traffic |
| Applies to an instance only if someone specifies the security group when launching the instance, or associates the security groupd with the instance later on | Automatically applies to all instances in the subnets its associated with (therefore, you don have to rely on users to specify the security group) |



## VPC Flow Logs
> Capture info about IP traffic going into your interfaces
> 	- VPC Flow Logs
> 	- Subnet Flow Logs
> 	- Elastic Network Interface Flow Logs
> Helps to monitor & troubleshoot connectivity issues. Example:
> 	- Subnets to internet
> 	- Subnets to Subnets
> 	- Internet to Subnets
> Captures network info from AWS managed interfaces to Load Balancers, ElastiCache, RDS, Aurora, etc..
> VPC Flow Logs data can go to S3, CloudWatch Logs, and Kinesis Data Firehouse

## VPC Peering
> Connect two VPC, privately using AWS's network
> Make them behave as if they were in the same network
> Must not have overlapping CIDR (IP address range)
> VPC Peering connection is not transitive (must be established for each VPC that need to another)\
> ![image](<images/Pasted image 20231027171212.png>)

## VPC Endpoints
> Endpoints allow you to connect to AWS services using private netwrok instead of the public www network
> This gives yo enhanced security and lower latency to access AWS services

### VPC Endpoint Gateway: S3 & DynamoDB
### VPC Endpoint Interface: the rest
![image](<images/Pasted image 20231027171631.png>)

## AWS Privatelink (VPC Endpoint Services)
> Most secure & scalable way to expose a service to 1000s of VPCs
> Does not require VPC peering, internet gateway, NAT, route tables
> Requires network load balancer (Service VPC) and ENI(Elastic Network Interface) (Customer VPC)\
> ![image](<images/Pasted image 20231027173235.png>)

## Site to Site VPN & Direct Connect

### Site to Site VPN
> Connect an on-prem VPN to AWS
> The connection  is automatically encrypted
> Goes over the public internet
> To use it
> 	- On-prem you must use a **Customer Gateway(CGW)**
> 	- AWS: must use a **Virtual Private Gateway(VGW)**
### Direct Connect (DX)
> Establish a physical connection between on-prem and AWS
> The connection is private, secure and fast
> Goes over a private network
> Takes at least a month to establish

![image](<images/Pasted image 20231027173635.png>)

## Client VPN
> Connect from you computer using OpenVPN to your private network in AWS on-prem
> Allow you to connect to your EC2 instances over a private IP (just as if you were in the private VPC network)
> Goes over public internet\
> ![image](<images/Pasted image 20231027175029.png>)

## Transit Gateway
> For havign transitive peering between thousands of VPC and on-prem, hub and spoke(star) connection
> One single gateway to provide this functionality
> Works with Direct Connect Gateway, VPN connections\
> ![image](<images/Pasted image 20231027175209.png>)

## SUMMARY
> 	- VPC: Virtual Private Cloud
> 	- Subnets: Tied to an AZ, network partition of the VPC
> 	- Internet Gateway: at the VPC level, provide internet access
> 	- NAT Gateway: give internet access to private subnets
> 	- NACL: Stateless, subnet rules for inbound and outbound
> 	- Security Groupds: Stateful, operate at the EC2 instance level or ENI
> 	- VPC Peering: Connect two VPC with non overlapping IP ranges,
> 	- Elastic IP: fixed public IPv4, ongoing cost if not in use
>	 - VPC Endpoints: Provide private access to AWS services within VPC
>	 - PrivateLink: Privately connect to a servicese in a 3rd party VPC
>	 - VPC Flow Logs: network trafic logs
>	 - Site to Site VPN: VPN over public internet between on-prem DC and AWS
>	 - Client VPN: OpenVPN connection from your computer into your VPC
>	 - Direct Connect: Direct private connection to AWS
>	 - Transit Gateway: Connect thousands of VPC and on-prem networks together
>	 