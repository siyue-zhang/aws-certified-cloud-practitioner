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

* [Security and Monitoring](#security-and-monitoring)
  * 

* [Additional Services](#additional-services)
  *

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

<img src=https://datadrivenai.files.wordpress.com/2019/11/using-aws-for-backup-and-restore-backup-in-the-cloud-backup-to-the-cloud-and-recovery-options-41-638.jpg?w=638 width=100/>


### Virtual Private Cloud (VPC)

### Elastic Compute Cloud (EC2)

### Elastic Block Storage (EBS)

### Costing Aspects



## Security and Monitoring

## Additional Services

## Practice Questions
