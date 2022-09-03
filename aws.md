# AWS Overview

## Lesson 1

AWS stands for Amazon Web Services. It has over 200 features. It is the most used cloud platform.

There is a shared responsibility model. AWS is responsible for the security of the cloud. The customer is responsible for security in the cloud.

AWS:

- Make sure that the hardware and global infrastructure of AWS works. Such as regions, availability zones and edge locations. This also makes sure that they are used when they are supposed to be used.
- Make sure that the software side of things works too, like databases, storage, networking and so on. Access should only be given to those who have the right roles. They should be secure and robust.

Customer:

- Responsible for the customer data.
- Server and client-side encryption.
- Network and firewall configuration.

The fundamental unit of AWS is the AWS account. It is like a container for all your AWS resources. It is a unit of organization, billing and access. From your account, you can grant permissions to isolate your workload.

AWS accounts have one root user. They have a unique email for only that specific account. They have billing information. You will also need contact information for your AWS account for it to be fully provisioned.

Each resource in AWS has a globally unique identifier called Amazon Resource Name (ARN). ARN model: `arn:partition:service:region:account-id:resource-id`.

## Lesson 2

AWS Data center has 10s of thousands of servers. They offer no services, this is managed by AWS.

Availability zone represents one or more data centers that are colocated together.

There is a logical name for the availability zone, and then there is the actual physical name. You have control to choose the logical name, but not the physical one.

An AWS Region is shown as multiple physically separate Availability Zones.

Edge locations are often used for caching. AWS has over 275+ edge locations, which is over 10 times more than AWS regions. It has much better distribution than regions.

# Lesson 3

Root user email address is used as username. Generic login URL. It has access to the entire AWS ecosystem and unique tasks. Root account properties can only be changed by the root user. If you close the account, the email cannot ever be used again.

IAM user represents a principal identity. Associated with permissions, group, inline and managed and a permission boundary. Container for credentials.

IAM Group is a collection of IAM users, associated with permissions, cannot be nested inside each other.

# Lesson 4
