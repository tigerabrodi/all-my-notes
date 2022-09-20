I'll share things I've learned while studying for the **AWS Certified Solutions Architect Associate**.

The notes will only contain things that were unfamiliar to me, as I've already studied for the AWS Cloud Practitioner and gone through The Cloud Resume Challenge.

# IAM

**AWS Managed Policies** are policies that are created and managed by AWS. It is good to use them if you're new to using policies.

**Customer Managed Policies** are policies that you create and manage in your AWS account. They provide more precise control. You can create/edit policies in the visual editor or through the JSON document directly.

Typically if one is working alone in an account, it fits to create an IAM user. For easier management if you need multiple users with the same permissions, you can create a user group.

You should use IAM roles to grant access to your AWS accounts by relying on short-term credentials. The credentials with roles are temporary. Roles are just a set of permissions that can be given to different services, and you don't need access keys. Let's say a user has to do an action, but we know for sure the user won't do it often, then the user can assume a role, giving them the permissions for that action for a short time. This is more secure than attaching the permissions directly to the user's access keys, which would be permanently.

# Amazon EC2

## Security Groups

Security groups act as a virtual firewall for your EC2 instances to control incoming and outgoing traffic.
