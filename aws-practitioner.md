# Introduction to Amazon Web Services

Benefits of AWS is you pay only for what you need, and don't need to pre-pay anything.

Cloud computing can be described as on-demand delivery of IT resources over the internet with pay-as-you-go pricing.

# Compute in the Cloud

## Introduction

The servers you use to gain access to virtual servers is called EC2. Using EC2 for server is highly flexible, cost-effective and quick.

All you have to do is request the EC2 instances you want, and they will launch and boot up, be ready to be used within a few minutes. Once you're done, you can easily stop or terminate the EC2 instances.

Your usage of EC2 can vary over time, and you only pay for what you use.

The EC2 instances run on top of physical host machines, which gets managed using virtual machines. When you spin up an EC2 instance, you aren't taking a host entirely by yourself, rather sharing it with others. The instances are secure and separate from each other.

The idea of sharing underlying hardware between virtual machines is called Multitenancy.

You can also configure the EC2 instances to your own needs.

## Amazon EC2 instance types

The Amazon EC2 instance families: General purpose, Compute optimized, Memory optimized, Accelerated computing and Storage optimized.

## Amazon EC2 pricing

Options: On-Demand, Amazon EC2 Savings Plans, Reserved Instances, Spot Instances, and Dedicated Hosts.

## Scaling Amazon EC2

Amazon EC2 Auto Scaling enables you to automatically add or remove Amazon EC2 instances in response to changing application demand. EC2 instances are elastic and scaleable, they shrink and grow depending on your needs, or better said, the amount of instances shrink and grow.

There are two types of scaling, dynamic and predictive. You can use each or both together, both together would result in scaling faster.

## Directing traffic with Elastic Load Balancing

When the client sends multiple requests to the backend, which EC2 instance should process these requests? How can we balance it out so that the work is evenly distributed among the instances?

For that, we need a load balancer.

A load balancer acts as a single point of contact for all incoming web traffic to your Auto Scaling group.

We can use Elastic Load Balancing, one of AWS load balancing services.

Itself scales up and down depending on the amount of instances that exist.

ELB runs on a regional construct, and not on individual EC2 instances, hence it is automatically highly available.

## Messaging and queuing

If applications communicate directly, this is called a tightly coupled architecture. The drawback here is that if the applications (frontend/backend) aren't in sync for some reason, for example if the backend isn't available at the time the frontend sends the request to the backend, then things can fall apart and get out of sync, and even the frontend may crash.

A more reliable architecture is the loosely coupled architecture. If one of the components of the system fails, it won't cause other components to fail.

We could introduce Message Queue. Application A wouldn't send requests or in this case **messages** directly to Application B, instead it would send them to the Message Queue, and if Application B isn't available for some reason, the messages don't get lost, and Application A could keep sending messages to the Queue. Once Application B is ready, the Queue can just make sure that the messages get sent to Application B and processed.

There are two different types of services in AWS that handle this: Amazon Simple Notification Service and Amazon Simple Queue Service.

### SNS

Subscribers would subscribe to topics and receive messages whenever a publisher publishes to that topic.

This allows multiple **components** to receive messages.

### SQS

A queue service, which stories messages in a queue. It cannot deliver messages, rather, an external service is needed to poll the SQS and grab messages from SQS.

This is good when you only need one subscriber, or if batching is important.

# Global infrastructure and reliability

## Introduction

AWS has spread out data centers all over the world, in order to be highly available and fault tolerant.

## AWS global infrastructure

There are 4 business factors that go into choosing a region.

- Compliance with data governance and legal requirements
- Proximity to your customers
- Available services within a Region
- Pricing

AWS calls a single data center or a group of data centers an Availability Zone (AZ). As a best practice to remain highly available, run across at least two AZs in a Region.

Regional scoped services are highly available by default since they run across all AZs.

## Edge locations

Amazon CloudFront uses edge locations to store cached copies of content closer to the customers for a faster delivery.

## How to provision AWS resources

You can interact with AWS services via AWS Management Console, AWS Command Line Interface, and SDKs that allow you to interact with the services using different programming language.

Ideally you shouldn't use the AWS Management Console to interact with its services, that would lead to a lot of clicking and manual steps, instead, make sure to have those steps written as code, whether using the CLI or SDK.

There are also services to automate this from AWS: AWS Elastic Beanstalk and AWS CloudFormation.

# Networking

## Introduction

Amazon VPC lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources. The resources can be either public or private facing, this is also called subnets. Meaning, either have access or no access to internet.

## Connectivity to AWS

To let public traffic access your VPC you attach an internet gateaway to the VPC.

To access private resources in a VPC, you can use a virtual private gateaway.

If you need to establish a dedicated private connection between your data center and a VPC, then you can use AWS Direct Connect.

## Subnets and network access control lists

A subnet is a section of a VPC in which you can group resources based on security or operational needs, they can be private or public.

In a VPC, subnets can communicate with each other.

A network access control list (ACL) is a virtual firewall that controls inbound and outbound traffic at the subnet level. ACLs are stateless, meaning they don't remember if they have let you in or out of the subnet, hence they will always check.

A security group is a virtual firewall that controls inbound and outbound traffic for an Amazon EC2 instance. Security groups are stateful, they do remember if they have let you into an EC2 instances, when you need to leave, they will let you out right away without checking you again.

## Global Networking

Customers are able to access the website because of Domain Name System, DNS. DNS resolution is the process of translating a domain name to an IP address.

Amazon Route 53 is a DNS web service. It gives developers and businesses a reliable way to route end users to internet applications hosted in AWS.

# Storage and databases

## Instance stores and Amazon Elastic Block Store (Amazon EBS)

An instance store provides temporary block-level storage for an Amazon EC2 instance.

An EBS snapshot is an incremental backup. This means that the first backup taken of a volume copies all the data. For subsequent backups, only the blocks of data that have changed since the most recent snapshot are saved.

## Amazon Simple Storage Service (Amazon S3)

In object storage, each object consists of data, metadata, and a key.

The data might be an image, video, text document, or any other type of file. Metadata contains information about what the data is, how it is used, the object size, and so on. An object’s key is its unique identifier.

## Amazon Elastic File System (Amazon EFS)

Amazon EFS is a regional service. It stores data in and across multiple Availability Zones.

In file storage, multiple clients (such as users, applications, servers, and so on) can access data that is stored in shared file folders.

## Amazon Relational Database Service (Amazon RDS)

In a relational database, data is stored in a way that relates it to other pieces of data.

Amazon Relational Database Service (Amazon RDS) is a service that enables you to run relational databases in the AWS Cloud.

## Amazon DynamoDB

Amazon DynamoDB is a key-value database service. It delivers single-digit millisecond performance at any scale.

DynamoDB is serverless, which means that you do not have to provision, patch, or manage servers.

## Amazon Redshift

Amazon Redshift is a data warehousing service that you can use for big data analytics.

# Security

## Shared responsibility model

The shared responsibility model divides into customer responsibilities (commonly referred to as “security in the cloud”) and AWS responsibilities (commonly referred to as “security of the cloud”).

## User permissions and access

AWS Identity and Access Management (IAM) enables you to manage access to AWS services and resources securely.

The root user is the owner of the entire account, it has complete access to every single AWS service and resource.

It is best to use the root user to create your first IAM user and assign it permissions to create other users.

An IAM user is an identity that you create in AWS.

It is best to create individual IAM users for each person who needs to access AWS.

An IAM policy is a document that allows or denies permissions to AWS services and resources.

It is best to follow the security principle of least privilege when granting permissions.

An IAM group is a collection of IAM users. When you assign an IAM policy to a group, all users in the group are granted permissions specified by the policy.

An IAM role is an identity that you can assume to gain temporary access to permissions. They are ideal for situations in which access to services or resources needs to be granted temporarily, instead of long-term.

## AWS Organizations

In AWS Organizations, you can centrally control permissions for the accounts in your organization by using service control policies (SCPs).

In AWS Organizations, you can group accounts into organizational units (OUs) to make it easier to manage accounts with similar business or security requirements.

## Compliance

AWS Artifact is a service that provides on-demand access to AWS security and compliance reports and select online agreements.

## Denial-of-service attacks

A denial-of-service (DoS) attack is a deliberate attempt to make a website or application unavailable to users.

In a distributed denial-of-service (DDoS) attack, multiple sources are used to start an attack that aims to make a website or application unavailable.

AWS Shield is a service that protects applications against DDoS attacks.

# Monitoring and analytics

## Amazon CloudWatch

Amazon CloudWatch is a web service that enables you to monitor and manage various metrics and configure alarm actions based on data from those metrics.

## AWS CloudTrail

AWS CloudTrail records API calls for your account. The recorded information includes the identity of the API caller, the time of the API call, the source IP address of the API caller, and more.

## AWS Trusted Advisor

AWS Trusted Advisor is a web service that inspects your AWS environment and provides real-time recommendations in accordance with AWS best practices.

Trusted Advisor compares its findings to AWS best practices in five categories: cost optimization, performance, security, fault tolerance, and service limits.

# Pricing and support

## AWS Free Tier

The AWS Free Tier enables you to begin using certain services without having to worry about incurring costs for the specified period.

## AWS pricing conepts

AWS offers a range of cloud computing services with pay-as-you-go pricing.

- Pay for what you use.
- Pay less when you reserve.
- Pay less with volume-based discounts when you use more.

## Billing dashboard

Use the AWS Billing & Cost Management dashboard to pay your AWS bill, monitor your usage, and analyze and control your costs.

## Consolidated billing

The consolidated billing feature of AWS Organizations enables you to receive a single bill for all AWS accounts in your organization. By consolidating, you can easily track the combined costs of all the linked accounts in your organization.

## AWS Budgets

In AWS Budgets, you can create budgets to plan your service usage, service costs, and instance reservations.

## AWS Cost Explorer
