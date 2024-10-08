AWS VPC Setup and Peering Configuration

This guide walks you through the process of setting up Virtual Private Clouds (VPCs), creating subnets, configuring VPC peering, updating route tables, security groups, and verifying connectivity between instances in separate VPCs.

![Diagram](https://github.com/user-attachments/assets/38bee6a4-cc1f-464d-98c4-ba0ed54a44f6)

Prerequisites
An AWS account with sufficient permissions to create VPCs, subnets, security groups, and EC2 instances.
Basic understanding of networking concepts such as CIDR blocks, routing, and security groups.

Steps to Set Up VPCs, Subnets, and VPC Peering

a. Set Up VPCs
1. Create VPC 1
Log in to the AWS Management Console.
Navigate to the VPC Dashboard.
Click on Your VPCs and then Create VPC.
Set the Name tag to "VPC-1".
Set the IPv4 CIDR block to 10.0.0.0/16.
Configure additional settings as needed (e.g., IPv6 CIDR block, Tenancy).
Click Create.
2. Create VPC 2
Follow the same steps as for VPC 1.
Set the Name tag to "VPC-2".
Set the IPv4 CIDR block to 192.162.0.0/16.
Click Create.

b. Create Subnets
1. Create Subnet in VPC 1
In the VPC Dashboard, navigate to Subnets.
Click Create subnet.
Select "VPC-1" from the dropdown.
Assign a Name tag such as "Subnet-1".
Choose an Availability Zone.
Set the IPv4 CIDR block to 10.0.1.0/24.
Click Create.
2. Create Subnet in VPC 2
Follow the same steps as for Subnet 1.
Select "VPC-2" from the dropdown.
Assign a Name tag such as "Subnet-2".
Set the IPv4 CIDR block to 192.162.1.0/24.
Click Create.

c. Set Up VPC Peering
1. Initiate VPC Peering Request
In the VPC Dashboard, navigate to Peering Connections.
Click Create Peering Connection.
Set the Name tag to "VPC-1-to-VPC-2-Peering".
Choose the VPC Requester (VPC 1).
For Peering Connection settings, select:
"My account" if both VPCs are in the same account.
"Another account" if they are in different accounts (you'll need the other account's ID).
Select the Accepter VPC (VPC 2).
Click Create Peering Connection.
2. Accept VPC Peering Request
In the Peering Connections page, select the newly created peering connection.
Click Actions and then Accept Request.

d. Update Route Tables
1. Update Route Table for VPC 1
In the VPC Dashboard, navigate to Route Tables.
Select the route table associated with VPC 1.
Click on the Routes tab and then Edit routes.
Add a new route:
Destination: 192.162.0.0/16
Target: Select the VPC peering connection ID.
Click Save routes.
2. Update Route Table for VPC 2
Follow the same steps as for VPC 1's route table.
Destination: 10.0.0.0/16
Target: Select the VPC peering connection ID.
Click Save routes.

e. Update Security Groups
1. Update Security Groups in VPC 1
In the EC2 Dashboard, navigate to Security Groups.
Select the security group associated with VPC 1.
Click on the Inbound rules tab and then Edit inbound rules.
Add a new rule:
Type: Custom TCP (or the specific type of traffic you want to allow)
Protocol: TCP (or appropriate protocol)
Port range: Set the port range (e.g., 80 for HTTP, 443 for HTTPS)
Source: 192.162.0.0/16
Click Save rules.
2. Update Security Groups in VPC 2
Follow the same steps as for VPC 1's security group.
Source: 10.0.0.0/16
Click Save rules.

f. Verify Connectivity
1. Launch Instances in Each VPC
Launch an EC2 instance in a subnet of VPC 1.
Launch another EC2 instance in a subnet of VPC 2.
2. Test Connectivity
SSH into the instance in VPC 1.
Attempt to ping the private IP address of the instance in VPC 2.
Ensure the security group rules allow ICMP traffic (for ping) or the specific type of traffic you are testing.
![peer1](https://github.com/user-attachments/assets/6698744d-c328-43d5-b7ef-7cd274c3a227)
![peer2](https://github.com/user-attachments/assets/bbdaed51-dad7-489e-9542-da6e27c42f2f)


Conclusion
By following these steps, you have successfully set up two VPCs, configured peering between them, and ensured connectivity between instances in each VPC. This setup is foundational for building more complex multi-VPC architectures.
