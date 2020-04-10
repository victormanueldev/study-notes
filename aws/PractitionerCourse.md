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
 The number of Edge Locations is greater than the number of Availability Zones, which is greater than the number of Regions.
 https://aws.amazon.com/about-aws/global-infrastructure/

**Choose the right AWS Region**
- Data Sovereignty Laws
- Latency to end users
- AWS Services availability

### Support Plans

- Basic (Free)
- Developer ($29/m)
- Bussines ($100/m) 24/7 vis phone  or chat
- Enterprise ($15.000ñ/m) - TAM Technical Account Manager

### Billing Alarms
To create a billing alarms, I have to go at CloudWatch in AWS Console, then to Billing link
and Create a New Alarm. In there, I can specify my condition related to my budget, 
I can set the period to check the billing state and set the notify way either SNS or other.
Services incurred from a cloud services provider are operating expenses

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
The bucket names share a common namespace. It cannot have the same bucket name as someone else.
I must choose a unique name for my buckets. The buckets are visible globally, but it can visible
in individual regions. It can replicate the content of one bucket to another automatically
by using cross region replication. It's possible change the storage class and encryption for 
objects on the fly. It's possible to host a static websites on S3. S3 scales automatically to
reach the demand, that suppots a large number of requests to the website 

***Restricting Bucket Access:***
- Bucket policies (Applies accross the whole bucket)
- Object Policies (Applises to individual files)
- IAM Polcies to Users & Groups (Applies to users and groups)

***Keys:***
- Key (Name of the object or file)
- Value (Data that is represented in Bytes)

***Models:***
- Read after write for PUT new objects
- Can take a seconds when UPDATE or DELETE an existing file

***Classes:***
- S3 Standard: Durability stored redundandly accross multiple devices
- S3 Infrecuently Access: For data that is less frecuently accessed
- S3 One Zone: IA a lower cost option for infrecuently accessed data and not requires multiple AZ
- S3 Intelligent Tiering: Optimize cost because automatically move data to the most const effective tier 
- S3 Glacier: Secure, durable and low-cost for data archiving and retrieval time configurable
- S3 Glacier Deep Archive: Is the AWS S3 lowest-cost where a retrieval time of 12 hours is acceptable.

### Cloud Front

It's a CDN that is a system of distributed servers that deliver webpage and others
web content to users based its geographical location

***Edge Location:***
- This is a location where contend will be cached, it's different to regions or AZ.
It's possible write an object to them. The objects are cached for the life of the TTL (Time to live)
that are meassured in seconds, and It can clear cached objects, but i will be charged ($$$)

***Origin:***
- This is the origin of all the files that the CDN will distribute. It can be either S3
Ec2, Load balanders or Route53.

***Distribution:***
- It's the term that refers to the collection of Edge Locations and can be 2 types:
    + Web Distribution:  Used for Websites
    + RTPM: Used for Media Streamming

### EC2
Is a web service that provide resizable compute capacity in the cloud.
Reduces the time required to obtain a boot new server instances to minutes.
Allows scale capacity. Is a server on the cloud.

It can be to 4 types: 
- On Demand: Pay a fixed rate by the hour or by the second of use.
- Spot: Enables you to bid (offer) whatever the price that I want pay for the instance capacity
- Reserved: Provides a capacity reservation and offer a discount by take a long time contract 1 or 3 Y
- Dedicated Host: Physical EC2 server dedicated for my use.

### EBS
It's a virtual hard disk that are used the EC2 instances.
There are 4 types:

- General Purpose SSD: Balance the perfornmanc and the price for a variey of workloads
- Provisioned IOPS SSD: Highest performance SSD Volume ofr mission critical low-latency and heavy workloads
- Throughput Optimized HDD: low cost designed for frecuently accessed and intensive workloads
- Cold HDD: Lowest cost HDD volume designed for a less frecuently accessed workloads (File servers)

Roles are much more secure than using access keys (.aws) or (aws configure) and are easier to manage.
I can add roles to EC2 instances at any time, and the EC2 permissions are updated inmediately.
The roles are universal.

### Elastic Load Balancers
ELB are of 3 flavours:

- Application Load Balancers: Operating at the requesting level, Make intelligent routing decisions.
- Network Load Balancers: Extreme performance or Static IP Address.
- Classic Load Balancers:  Test & Dev for keep low costs.

### RDS
Relational Databases Instances features:
- Multi AZ: It's for a Disaster recovery
- Read Replicas: It's for performance

There are the Non Relational Databases: DynamoDB.

Data Warehouse: For bussines intelligence, complex analytics queries. Redshift

Elastic Cache: Is a caching engine on the cloud for view most common queries and it's gonna take a 
big load off production database.

### AMI
It's a EC2 instance image or snapshot take in a specific time, it's useful whem a instance is 
terminated or stopped and we need to create a new instance but keeping the last insntance state.

### Auto Scaling
It's useful to deploy many instanaces across any AZ and it do that our web server to be 
fault-tolerant, because Auto scaling create instances with a Target Group Policies, and 
it ensures that the website be healtly all the time

### Route 53
It's an Amazon DNS Service and is global, we can register a domain name and redirect all
the traffic around the world.

### Elastic Beanstalk
It can deploy and manage any resourses that we need to upload an application ie. PHP Based App
Elastic Beanstalk automatically hamdle the details of capacity provisioning, load balancing,
scaling and App healt monitoring, but it is limited in what it can provision and isn't 
programmable

### Cloud Formation
Is a service that helps us to model and set up AWS resources and we can spend less time managing
those resources. It takes care of provisioning and configuring those resources. AWS Cloud Formation
handles all for you. (IaC). This service es completly programmable and FREE!!

### Cloud Watch
Is used for monitoring performance and it can monitor most  of AWS as well as you application that
runs on AWS. We can have one minute interval by turning on detailed monitoring, we can create
alarms which trigger notifications. Cloud Watch is all about performance.

### System Manager
It can be used to manage fleet (set) of EC2 instances & VM, any piece of software are installed 
on each VM, can be both inside AWS and On premise. Run commands to install, patch and uninstall 
software and it integrates with cloud watch to gives a dashboard of the entire state.

*** AWS Global AWS Services ***
- IAM: Manage the users, groups, roles and policies are global.
- Route 53: DNS AWS provider.
- CloudFront: Global CDN
- SNS: Simple Notification Service
- SES: Simple Email Service

*** AWS Global and Regional Services ***
- S3: Is global but we can configure it for access in a specific region

*** AWS Resources to using on Premise ***
- Snowball: Is a big hard disk for storage large files
- Snowball edge: Is a snowball but add a CPU and it's useful for run lambda functions on premise
- Storage Gateway: It's for caching files and save them on S3 buckets
- CodeDeploy: It's for deploy our code either be to AWS or onpremise servers
- Opsworks: It works like beanstalk but it's used for on premise data centers.
- IoT Greengrass: Is to connect the physical devices to AWS.

- Link to AWS whitepaper and best practices
https://d1.awsstatic.com/whitepapers/architecture/AWS_Well-Architected_Framework.pdf
https://d1.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf




