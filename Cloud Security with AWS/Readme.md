Cloud Security with AWS IAM
Project Overview
This project demonstrates the implementation of AWS Identity and Access Management (IAM) policies to enforce cloud security. The main objective is to manage permissions effectively for users interacting with EC2 instances, specifically ensuring that only certain actions can be performed on different environments (production and development).

Project Components
EC2 Instances:

Production EC2: An EC2 instance tagged as "Production".
Development EC2: An EC2 instance tagged as "Development".
IAM Policy:

A custom IAM policy was created to control user permissions.
The user group associated with this policy has the following permissions:
Allow: Full access to EC2 instances.
Deny: Permission to change the instance state (e.g., stop, start, terminate) of the EC2 instance tagged as "Development".
Project Setup
Prerequisites
An AWS account with IAM administrative access.
Basic knowledge of AWS EC2 and IAM services.
Steps to Reproduce
Create EC2 Instances:

Launch two EC2 instances.
Tag one instance with Environment=Production.
Tag the other instance with Environment=Development.
Create IAM Policy:

Navigate to the IAM service in the AWS Management Console.
Create a new policy with the following JSON configuration:
{
    
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "ec2:*",
            "Resource": "*"
        },
        {
            "Effect": "Deny",
            "Action": "ec2:StopInstances",
            "Resource": "arn:aws:ec2:<region>:<account-id>:instance/<instance-id>",
            "Condition": {
                "StringEquals": {
                    "aws:ResourceTag/Environment": "Development"
                }
            }
        },
        {
            "Effect": "Deny",
            "Action": "ec2:TerminateInstances",
            "Resource": "arn:aws:ec2:<region>:<account-id>:instance/<instance-id>",
            "Condition": {
                "StringEquals": {
                    "aws:ResourceTag/Environment": "Development"
                }
            }
        },
        {
            "Effect": "Deny",
            "Action": "ec2:RebootInstances",
            "Resource": "arn:aws:ec2:<region>:<account-id>:instance/<instance-id>",
            "Condition": {
                "StringEquals": {
                    "aws:ResourceTag/Environment": "Development"
                }
            }
        }
    ]
}
Replace <region>, <account-id>, and <instance-id> with your specific AWS region, account ID, and instance IDs.
Attach the IAM Policy to a User Group:

Create a new IAM user group or use an existing one.
Attach the policy created in the previous step to this group.
Add Users to the Group:

Add the necessary users to the IAM user group.
Testing and Validation
Access Production EC2 Instance:

Log in as a user from the IAM group.
Confirm that you have full access to the EC2 instance tagged as "Production", including the ability to change its state.
Access Development EC2 Instance:

Attempt to change the state of the EC2 instance tagged as "Development".
Confirm that the action is denied according to the IAM policy.
Conclusion
This project demonstrates how to leverage AWS IAM policies to enforce cloud security by managing access to EC2 instances in different environments. By carefully controlling permissions, you can ensure that users have the necessary access without compromising the integrity of your development environments.

Future Enhancements
Expand the IAM policy to manage access to other AWS services based on environment tags.
Implement monitoring and alerting for unauthorized access attempts.
