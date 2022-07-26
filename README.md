# AWS Certified Cloud Practitioner
Learning Notes for [AWS Certified Cloud Practitioner](https://aws.amazon.com/certification/certified-cloud-practitioner/?ch=cta&cta=header&p=2)

<img src=https://d1.awsstatic.com/training-and-certification/Certification%20Badges/AWS-Certified_Cloud-Practitioner_512x512.bc006f14f986fa4f3ca238b0b62be458ce1fb5ce.png width=150/>

This credential helps organizations identify and develop talent with critical knowledge related to implementing cloud initiatives. Earning AWS Certified Cloud Practitioner validates cloud fluency and foundational AWS knowledge.

## Contents

* [Cloud Concepts](#cloud-concepts)
  *  Amazon Web Services
  *  AWS Free Account
  *  Regions and Availability Zones
  *  AWS Support Plans

* [Cloud Architecture Design](#cloud-architecture-design)
  * Service Continuity
  * AWS Organizations
  * Total Cost of Ownership
  * Cost Allocation Tags
  * AWS Trusted Advisor

* [AWS Core Services](#aws-core-services)
  * Simple Storage Service
  * Amazon Glacier
  * Virtual Private Cloud
  * Elastic Compute Cloud
  * Elastic Block Storage
  * Costing Aspects
  * Elastic Load Balancer
  * Route53
  * Autoscaling
  * Cloudfront
  * Relational Database Dervice
  * DynamoDB
  * Lambda
  * Elastic Beanstalk
  * Simple Queue Service
  * Simple Notification Service
  * Cloudformation
  * Cognito

* [Security and Monitoring](#security-and-monitoring)
  * Shared Responsibility Model
  * Identity and Access Management
  * Cloudwatch
  * Cloudtrail
  * VPC and EC2 Security
  * Other Security Aspects

* [Additional Services](#additional-services)
  * AWS OpsWorks
  * 6 Advantages of Cloud Computing
  * EBS Snapshots
  * Elastic File System
  * NAT Instances and NAT Gateway
  * Elastic IP Address
  * AWS Storage Gateway
  * AWS Snowball Device
  * Amazon GuardDuty

* [Practice Questions](#practice-questions)


## Cloud Concepts

### Amazon Web Services

* Elastic compute cloud
* Simple storage service
* Relational database service
* Virtual private cloud (own isolated network)

### AWS Free Account

Free tier details

* Always free
* 12 months free
* Trials

EC2: type = **t2.micro** AND usage of hours per month < 750

### Regions and Availability Zones

Which regions to host your resources:

* Close proximity to users
* Data requirement for a specific region

A region consists of multiple availability zones.

An availability zone is a collection of multiple physical data centers. Data is replicated across multiple data centers to ensure availability.

### AWS Support Plans

1. Developer 
2. Business
3. Enterprise (15K/month, technical account manager)

APN: partner network program

## Cloud Architecture Design

### Service Continuity

* Fault tolerance - if a fault occurs at the infra level, you still need to ensure services can be made available
* High availability - if infra goes down, you need to ensure the right measures are in place to ensure the application is still available

1. Make use of availability zones, deploy EC2 instances across availability zones
2. For higher availability and for **disaster recovery**, deploy secondary solutions to multiple regions
3. Make use if Elastic Load Balancer for distributing traffic to your underlying EC2 instances

Important design concepts:

* Always decouple components of your application
* Don't have a tight intregration between application components
* Always design with failure in mind
* Make use of features available in AWS

### AWS Organizations

* Account management service
  * For company with multiple AWS accounts for different departments
* Get consolidated bills
* Volume pricing discounts
* Service control policies at the organization level

### Total Cost of Ownership (TCO) Calculators

Cloud VS On-premise infra

TCO calculators allow you to estimate the cost savings when using AWS and provide reports that can be used in executive presentations.

### Cost Allocation Tags

* Tags are used to organize resources in AWS
* Can be used to track resources at a detailed level

### AWS Trusted Advisor

Recommendations to user:

* Cost optimization
* Performance
* Security
* Fault Tolerance
* Service Limits

:point_up_2: [back](#contents)

## AWS Core Services

### Simple Storage Service (S3)

<img src=https://miro.medium.com/max/333/1*1A1CQ8a-vKphpDu97_U6Kw.png width=100/>

* Object level storage
* Store and retrieve any amount of data
* Highly scalable and reliable

Use Case:
* Allow users to upload photos

S3 (global) --> **Bucket** (specific region) --> **Object**

Object class:
1. Stanrdard - default class, objects in the bucket are accessed frequently
2. Reduced Redundancy - non-critical data, if you want to lower cost for storage
3. Infrequently Access (STANDARD_IA/ONEZONE_IA)
4. GLACIER and DEEP_ARCHIVE - for data archival, storage at much lower costs

Object is not encrypted in server by default.

**Static Website Hosting**

### Amazon Glacier

<img src=https://seeklogo.com/images/A/aws-glacier-logo-2F1F85B2C4-seeklogo.com.png width=60/>

* Used for cold or archive storage, over month or year
* Much cheaper storage option

1. In AWS Console, you create a **vault** to hold the objects.
2. To upload an object, you need to use the AWS CLI or AWS SDK.
3. Or use Lifecycle management feature in S3.
4. To retrieve an object you have to submit a job request.
5. With the standard retrieval, it could take around **3-5 hours to download an object**.
6. Urgent request: expedited retrieval at a higher cost to get object within a matter of minutes

### Virtual Private Cloud (VPC)

<img src=https://nicovmc.files.wordpress.com/2019/06/image-1.png width=60/>

* Isolated Virtual Network dedicated to your AWS account
* Isolated from other Virtual Networks
* You can then launch resources such as EC2

1. VPC will be allocated a CIDR block (e.g. 10.0.0.0/16)
2. You can have multiple VPCs defined in AWS
3. When you create an AWS account, you get default VPC created per region
4. In VPC, you can then define subnets
5. Subnet will be assigned CIDR block which is a subset of the VPC CIDR block

<p align=center>
<img src=https://docs.aws.amazon.com/vpc/latest/userguide/images/default-vpc-diagram.png width=500/>
<p/>
 
> Classless Inter-Domain Routing (CIDR) is a method for allocating IP addresses and for IP routing.

### Elastic Compute Cloud (EC2)

<img src=https://camel.apache.org/camel-kamelets/0.5.x/_images/kamelets/aws-ec2-sink.svg width=60/>

* Ability to create a virtual server on the cloud
* On-demand option
* Cloudwatch service can help monitor instances
* Different instances types based on the type of workload

To define:
* Machine image (Windows, Linux)
* Instance type (CPU, memory, etc.)
* VPC
* Security group (like firewall, control the flow of traffic)
* Volume (storage)
* Tags (metadata)

On-demand pricing
* Most flexible option
* Not the cheapest option

Spot pricing
* You can run workloads on EC2 instances and also have up to 90% savings on costs
* The instances are available based on spare capacity available in AWS
* 6-hour notice for interruption
* If AWS runs out of capacity the compute capacity will be taken away
* Good to choose Spot Instances if your workloads can be interrupted

Reserved pricing
* You can pay an upfront price and reserve an instance type
* Save up to 75%
* Standard RI (reserved instance): fixed type of workload
* Convertible RI: allow to change the attributes of RI to greater values only
* Scheduled RI: launch instances during specific time windows

### Elastic Block Storage (EBS)

<img src=https://upload.wikimedia.org/wikipedia/commons/thumb/0/0f/AWS_Simple_Icons_Storage_Amazon_EBS.svg/1200px-AWS_Simple_Icons_Storage_Amazon_EBS.svg.png width=60/>

* Block storage for EC2 Instances - Create **Volume**
* You can have multiple volumes for an instance
* Root volume is assigned when EC2 instance is created
  * **General purpose SSD** - for typical workloads such as Web servers
  * **Provisioned IOPS** - for more resource intensive workloads such as databases (higher input and output operations)
  * **Throughput optimized HDD** - for more throughput on the volume such as Big Data applications
  * **Cold HDD** - for archive storage

After creating a volume in the same availability zone, you need to go to the server manager of OS to bring the new disk online. Then you can create a volume in the new disk.

<p align=center>
<img src=./volume.jpg width=700/>
<p/>
 
### Costing Aspects

* Pricing Calculator - indicative pricing on hosting resources in AWS
* Billing Section - see the costs to date and billing details
* Cost Explorer - allow you to analyse spend, but you need to enable this in advance

### Elastic Load Balancer

<img src=https://coralogix.com/wp-content/uploads/2019/02/Load-Balancer@2x.png width=60/>

* Distribute requests to the underlying EC2 instances or lambda
* Managed service

Scheme:
* Internet facing load balancer
* Internal load balancer

> Key pair is also a region specific resource. Tools: PuTTY, PuTTYgen, WinSCP to login linux server in Windows. Load .pem file into PuTTYgen. WinSCP is used to change file content in the server.

### Route53

<img src=https://www.testpreptraining.com/blog/wp-content/uploads/2020/03/What-is-Amazon-Route-53_-1.png width=400/>

* Managed DNS Web service
* Register domain names
* Route traffic to resources hosted in AWS
* Can be used to check the health of your resources, e.g., check load balancer

1. Create a hosted zone
2. Register the Nameservers in the domain registrar
3. Create a resource record in the hosted zone

<img src=https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fdfecb48f-842b-4147-b0c1-7a4615774c91_479x541.png width=400/>

Routing Policies

* Simple routing policy - for a single resource
* Failover routing policy - for active-passive failover
* Geolocation routing policy - route traffic based on the location of users
* Weighted routing policy - route traffic to different resources based on a weightage
* Latency routing policy - route traffic to the region that provides the lowest latency

Can be used for A/B Testing.

### Autoscaling

<img src=https://p2zk82o7hr3yb6ge7gzxx4ki-wpengine.netdna-ssl.com/wp-content/uploads/AWS-ASGs-2.png width=100/>

* This service allows to scale EC2 instances based on demand
* You can create Autoscaling Groups
* You can create conditions

1. Define a launch configuration
2. Define the Autoscaling Group
3. For Scaling Group, you can perform a **manual scaling**
4. You can also perform a **scheduled scaling**
5. You can also scale based on **metrics**

CloudWatch creates alarm -> Autoscale based on alarm

### Cloudfront

<img src=https://cdn.worldvectorlogo.com/logos/aws-cloudfront.svg
 width=60/>
 
* Used for effective distribution of content to users across the world
* Distribute content with the help of edge locations

Process:
1. User makes request
2. Request routed to the nearest edge location
3. If the web content is in the cache of the edge location, it's sent to the user
4. If not, edge server makes a request to the origin
5. Once the data is received, is sent to user and cached for further use

### Relational Database Service

<img src=https://uploads-ssl.webflow.com/5eb586cf8a64e8125e18ebe7/5ec041c01799656fb494c37e_AWS_Simple_Icons_Database_AmazonRDS.svg_-20160325070440.png width=60/>

* Setup a relational database
* Support for MySQL, Oracle, MariaDB, PostgreSQL, MS SQL Server
* A lot of admin jobs are managed by AWS

Features:
* Scale the underlying instance hosting the database instance at any ptime
* Monitor via CloudWatch
* Enable automated backups
* Can create snapshots of database
* Enable high availability of database by using Multi-AZ feature (secondary database in another availbility zone, auto sync)

RDS will be deployed in an EC2 instance, but EC2 is managed by AWS.

### DynamoDB

<img src=https://upload.wikimedia.org/wikipedia/commons/f/fd/DynamoDB.png width=60/>

* Fully managed NoSQL database
* In DynamoDB, you directly start working with tables
* A table is a collection of items, each item is a collection of attributes
* JSON data format
* Simple Primary Key - Partition Key
* Composite Key - Partition Key and Sort Key, if same partition
* Very fast operation

* Charged by read and write throughput
* Represented as Capacity Units, 1 RCU - one strongly consistent read request, for an item up to 4KB
* Write Capacity Units, 1KB

When not to use DynamoDB:
* Complex queries on the data
* Table joins

### Lambda

<img src=https://upload.wikimedia.org/wikipedia/commons/thumb/5/5c/Amazon_Lambda_architecture_logo.svg/1200px-Amazon_Lambda_architecture_logo.svg.png width=60/>

* Serverless compute service
* Support a host of programming languages such as Node.js, Python, Ruby, Java, Go and .Net
* Avoid deploying and maintaining EC2
* Only get charged for the time the code is run
* You don't have access to the underlying infrasturcture
* Maximum memory is 3 GB
* Time out for lambda funtion - Maximum 15 minutes

### Elastic Beanstalk

* Good when you want developers to have environments up and running quickly
* Support a variety of programming languages
* Support application servers such as Tomcat and Internet information sevices

### Simple Queue Service

* Applications (producer) send messages to Queue
* Consumer receives messages
* Standard queues
* FIFO queues - used to preserve the order of messages
* Visibility timeout: the time message is invisible for other consumers

### Simple Notification Service (SNS)

* Different endpoints can subscribe to the Simple Notification service
* Consumers can receive messages via different protocols
* Define **Topic**, **subscribers** receive message from Topic via different protocol

### Cloudformation

* Allow to spin up infra in AWS via templates
* **Template** desribes all details of resources to be created

Template --> Cloudformation --> Stack

* Template in JSON or YAML format

### Cognito

Web authentication service (e.g., using Facebook account for app login)

### Amazon Redshift

* Data warehousing service
* Data by column, insert row very slow

### Amazon Kinesis

* Used to collect, process and analyse real time data
  * Kinesis Data streams
  * Kinesis Video streams
  * Kinesis Data firehose - capture, transform and load stream of data to AWS data stores
  * Kinesis Data Analytics - process data streams in real time with SQL or Java

### Amazon Aurora

* A database engine with AWS RDS
* Compatible with MySQL and PostgreSQL
* Delivers **higher throughput** than the traditional MySQL and PostgreSQL database engines

### Amazon ElastiCache

* In-Memory data store
* Fully managed Redis and Memcached service
* Normally sued for gaming type applications, IoT apps

### Amazon EMR

* Used to run Big Data frameworks such as Apache Hadoop and Apache Spark
* Used to process and analyse large amounts of data

:point_up_2: [back](#contents)

## Security and Monitoring

### Shared Responsibility Model

AWS responsible for:
* underlying physical infra
* decommissioning of old hardware
* patching of firmware
* data center security

Customer responsible for:
* Patching of EC2 instances
* Encryption of data at rest/in transit
* Looking after the costing aspect

### Identity and Access Management (IAM)

* Control access to services in AWS
* Use in-built policies or create new one
* Identities
  * AWS root user
  * IAM User - represent a person or user
  * IAM Group
  * IAM Role -  similar to IAM user, but does not associate itself with any credentials
* Policies
  * Used to control permissions
  * Can be attached to users, groups or roles
  * Can be assigned to resources as well

Good practice:
* Don't use root account for day to day activities
* Enable multi-factor authentication
* Ensure users are granted only the required priviledges
* Password policies

Access type:
* Programmatic access
* AWS Management Console access

> Authentication in AWS is done via (IAM users, groups and roles) whereas Authorization is done by Policies.

### CloudWatch

* Monitoring service
* Get metrics for various services (custom metrics)
* Create alarms (billing alarms)
* Used to store logs (install agents on EC2 Instanes to send logs)
* **Cloudwatch Events** to trigger a Lambda function to start the EC2 Instance 

### CloudTrail

* Service used from a governance and compliance perspective
* All actions taken in AWS account are recorded by Cloudtrail (e.g., login logs)
* Events get retained for 90 days, longer store needs to be set up
* CloudTrail sends events to an S3 bucket

### VPC and EC2 Security

Network Access Control Lists
* Used to protect traffic into subnets hosted in a VPC (Policy Group controls traffic into EC2 instances)
* NACL decides what traffic can flow out and flow in subnet
* Each rule decides which protocol, port range and source

### Other Security Aspects

**Web Application Firewall**
* Attacks from the Internet
* Cross site scripting
* SQL Code injection

**AWS Shield**
* Can be used to protect against DDoS attacks
* AWS Shield standard is given free

**AWS Artifact**
* Use this service to download AWS Security and compliance documents
* AWS ISO certidications or Service Organization Control reports

:point_up_2: [back](#contents)

## Additional Services

### AWS OpsWorks

* Configuration Management Service
* Allow to enforce the desired state of your infra
* Allow to integrate existing tools such as Chef and Puppet

Chef: automate **stack** configuration for production, development and etc. A stack can include OS, Web Server, SQL Server...

### 6 Advantages of Cloud Computing

1. Trade capital expense for variable expenses
2. Benefits from massive economies of scale
3. Stop guessing capacity (everything on-demand in cloud)
4. Increase speed and agility (no need to wait for infrastructure)
5. Stop spending money running and maintaining data centers
6. Go global in minutes

### EBS Snapshots

* Can use EBS Snapshots to take a backup of the data on Amazon EBS Volumes
* Point-in-time snapshots are taken and stored in S3
* Can recreate an EBS Volume based on the snapshot
* Snapshots that are created out of encrypted volumes are automatically encrypted

### Elastic File System

* Used for AWS Cloud services or on-premise resources
* Can grow and shrink automatically based on demand
* It supports Network File System
* **Multiple EC2 Instances** can access the Amazon EFS file system at the same time

<p align=center>
<img src=https://miro.medium.com/max/1031/1*Gig18TiVgWdxXeedc778UA.png>
<p/>

### NAT Instances and NAT Gateway

* Network Address Translation can be used to enable instances in the private subnet to initiate outbond IPv4 traffic to the Internet
* NAT Instance is provisioned in the public subnet
* NAT Instance needs to have internet access
* There is a special AMI available to create NAT Instances

**Internet Gateway**: a bidirectional channel with public network

NAT Gateway is the managed instance.It's a unidirectional channel to send out data from private network to public network.

### Elastic IP Address

* Public IP address will change when Instance is rebooted.
* Elastic IP is like a static IP for your instance. 
* Create and associate

<p align=center>
<img src=./ip.JPG width=600>
<p/>

### AWS Storage Gateway

* This service helps to connect an on-premises software appliance with cloud-based storage
* This helps to easily scale your storage with the use of AWS cloud

1. File Gateway - file interface into S3
2. Volume Gateway - Internet Small Computer System Interface (iSCSI)
3. Tape Gateway - a durable, cost-effective solution for archiving data onto AWS

### AWS Snowball Device

* Physical devices
* Transfer data between physical storage devices and the Amazon S3
* Snowball Device is used for **transferring large amounts of data** (through Internet uploading too slow)
* Recommend more than 10TB data

Features of Snowball Edge:
* Durable local storage
* Local compute with AWS Lambda
* Can use it in a cluster of devices

AWS Snowball process
1. You create a job in AWS Snow Family Mnagement Console
2. Snowball device is sent to the customer
3. Then transfer the data onto the device
4. Then ship the container back to AWS
5. AWS will transfer the data onto Amazon S3

### Amazon GuardDuty

* This is a cloud service that monitors and analyses processes from data sources (VPC Flow logs, CloudTrail event logs, DNS logs...)
* It uses algorithms to determine threats based on the analysed data (e.g. it can help detect compromised EC2 Instances)



:point_up_2: [back](#contents)

## Practice Questions

:point_up_2: [back](#contents)


