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

* [AWS Core Services](#aws-core-services)
  * 

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
* Trails

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

## AWS Core Services

## Security and Monitoring

## Additional Services

## Practice Questions
