
## AWS STS (Security Token Service)
> Enables you to create temporary, limited-privileges credentials to access your AWS resources
> Short-term credentials: you configure expiration period
> Use cases
> 	- Identify federations: manage user identities in external systems, and provide them with STS tokents to access AWS resources
> 	- IAM Roles for cross/same account access
> 	- IAM roles for Amazon EC2: provide temporary credentials for EC2 instances to access AWS resources\
>![image](<images/Pasted image 20231031224846.png>)

## Amazon Cognito
> Identity for your Web and Mobile apps users (potentially millions)
> Instead of creating them an IAM user, you create a user in Cognito\
> ![image](<images/Pasted image 20231031230330.png>)

## Microsoft Active Directory (AD)
> found on any Windows Server with AD Domain Services
> Database of objects: User Accounts, Computers, Printers, File Shares, Security Groups
> Centralized security managements, create account, assign permissions.

## AWS Directory Services
> ![image](<images/Pasted image 20231031230700.png>)

## AWS IAM Identity Center (Successor to AWS Single Sing-on)
> One login (single sign-on) for all your
> 	- AWS accounts in AWS Organizations
> 	- Business cloud apps
> 	- SAML2.0-enables apps
> 	- EC2 Windows Instances
> Identity Providers
> 	- Built-in identity store in IAM identity Center
> 		- 3rd party: Active Directory(AD), OneLogin, Okta
> **Whenever you see one access to multiple AWS accounts you have to think about the IAM identity
center**\
>  ![image](<images/Pasted image 20231031231007.png>)

## SUMMARY
> IAM
> 	- Identity and Access Management inside your AWS account
> 	- For users that you trust and belong to your Company
> Organizations: Manage multiple accounts
> Security Token Service(STS): temporary, limited privileges creds to access AWS resources
> Cognito: create a database of users for your mobile & web apps
> Directory Services: Integrate Microsoft Active Directory in AWS
> IAM Identity Center: one login for multiple AWS accounts & apps
