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

Create EC2 Instances:
Launch two EC2 instances without a keypair
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
      "Resource": "*",            
      "Condition": {                
        "StringEquals": {                    
          "ec2:ResourceTag/Env": "development"                
        }            
      }        
    },        
    {            
      
      "Effect": "Allow",            
      "Action": "ec2:Describe*",            
      "Resource": "*"        
    },        
    {            
      
      "Effect": "Deny",            
      "Action": [                
        "ec2:DeleteTags",                
        "ec2:CreateTags"            
      ],            
      "Resource": "*"        
    }    
  ] 
}

Attach the IAM Policy to a User Group:

Create a new IAM user group or use an existing one.
Attach the policy created in the previous step to this group.
Add Users to the Group:
Add the necessary users to the IAM user group.
![iam3](https://github.com/user-attachments/assets/d3b793f6-4e53-4923-9e78-667d5d81b9dc)

Testing and Validation
Accessing the AWS Console with an Alias
IAM users accessed the AWS Management Console using an alias for better security management and ease of use.
![iam2](https://github.com/user-attachments/assets/3370c4bb-ba65-464f-b006-66cb33817d5b)
![iam4](https://github.com/user-attachments/assets/4ddfe3e8-76b7-4ee9-a91b-80a1b4861839)

Confirm that you have full access to the EC2 instance tagged as "Production", including the ability to change its state.
![iam7](https://github.com/user-attachments/assets/e00a6a06-17aa-4085-b6fb-a16e7e1d8f44)
Access Development EC2 Instance:
Attempt to change the state of the EC2 instance tagged as "Development".
Confirm that the action is denied according to the IAM policy.
![iam6](https://github.com/user-attachments/assets/ba112b36-197b-4642-bcbc-dcc568a8307c)

Conclusion
This project demonstrates how to leverage AWS IAM policies to enforce cloud security by managing access to EC2 instances in different environments. By carefully controlling permissions, you can ensure that users have the necessary access without compromising the integrity of your development environments.

Future Enhancements
Expand the IAM policy to manage access to other AWS services based on environment tags.
Implement monitoring and alerting for unauthorized access attempts.
