# Notes

### Definition
Cloud computing is the on-demand delivery of compute database storage,
applications and other IT resource through a cloud services platform,
via the internet with pay-as-you-go princing...

At end of the day, cloud computing is the renting of computers 
to send msg, storage files, etc...

- Link to Overview of AWS
https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html

### 6 Adventages of Cloud Computing

- Instead of having invest a lot of money in data centers, I can pay only when 
I consume computing resources, and only for how much I consume.
- AWS has the best prices in the marked, because they build their own servers.
- Stop guessing about capacity, cloud can scale with your busines needs with no long term contracts.
- Increase the speed and agility.
- Stop spending money running and maintening data centers.
- Go global in minutes, with the easy deploy of applications in multiple regions with just few clicks.

### Global infrastructure
25 Regions and 70 Availability zones at 2020 
 ***Region:*** is a phisical location in the world which consists in one or more AZ.
 ***Availability Zones:*** Is a one or more discrete data centers.
 ***Edge Locations:*** Are locations for AWS wich are used for caching content.

**Choose the right AWS Region**
- Data Sovereignty Laws
- Latency to end users
- AWS Services availability

### Support Plans

- Basic (Free)
- Developer ($29/m)
- Bussines ($100/m)
- Enterprise ($15.000ñ/m) - TAM Technical Account Manager

### Billing Alarms
To create a billing alarms, I have to go at CloudWatch in AWS Console, then to Billing link
and Create a New Alarm. In there, I can specify my condition related to my budget, 
I can set the period to check the billing state and set the notify way either SNS or other.

### Identity Access Management IAM
It's global, I don't have specify the region to create users or groups.
Access to the platforms in 3 ways:
- Via the console (Web Browser)
- Programaticlly (Using the commandline)
- Using SDK (for use AWS inside the apps)

The root account is the email that I used in the AWS register, The root always have all permissions
to all services, I should create individual users instead to share the root credentials, is good use 
the Multi-factor Authentication to log in the console (MFA)

***Group:*** Place where I place the AWS Users, and the users will inherit all permisions that the
group has.

***Policy:*** Contents the permission that a group has and it's write in JSON format

### S3
S3 is a Object-based: ie. allows to upload files, that could be weigth from 0B to 5TB. 
There is unlimited storage, files are stored in a buckets, S3 is a universal namespace.
No situable to install an OS, for Successfull uploads generate a  HTTP 200 status code.

***Keys: ***
- Key (Name of the object or file)
- Value (Data that is represented in Bytes)

***Models: ***
- Read after write for PUT new objects
- Can take a seconds when UPDATE or DELETE an existing file

***Classes: ***
- S3 Standard: Durability stored redundandly accross multiple devices
- S3 Infrecuently Access: For data that is less frecuently accessed
- S3 One Zone: IA a lower cost option for infrecuently accessed data and not requires multiple AZ
- S3 Intelligent Tiering: Optimize cost because automatically move data to the most const effective tier 
- S3 Glacier: Secure, durable and low-cost for data archiving and retrieval time configurable
- S3 Glacier Deep Archive: Is the AWS S3 lowest-cost where a retrieval time of 12 hours is acceptable 