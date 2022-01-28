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

* Register domain names
* Route traffic to resources hosted in AWS
* Check the health of your resources

1. Create a hosted zone
2. Register the Nameservers in the domain registrar
3. Create a resource record in the hosted zone

Routing Policies

* Simple routing policy - for a single resource
* Failover routing policy - for active-passive failover
* Geolocation routing policy - route traffic based on the location of users
* Weighted routing policy - route traffic to different resources based on a weightage
* Latency routing policy - route traffic to the region that provides the lowest latency

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

## Security and Monitoring

## Additional Services

## Practice Questions
