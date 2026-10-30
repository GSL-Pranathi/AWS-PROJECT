AWS VPC Peering Project

Introduction

The goal of this project is to demonstrate how to create a VPC peering connection between two Amazon Virtual Private Clouds. The task is to achieve a private network connection between different VPCs using route tables and security groups.

Objectives

- Create two different AWS VPCs.
- Configure public and private subnets.
- Start EC2 instances.
- Create VPC peering.
- Configure routing tables and security groups.
- Test private connectivity between instances.

Architecture

VPC A - "ewb-vpc-a"

- CIDR block – "10.10.0.0/16".
- Public subnet – "10.10.1.0/24".
- Private subnet – "10.10.2.0/24".
- Internet Gateway - "ewb-igw-a".
- Public and private route tables.

VPC B - "ewb-vpc-b"

- CIDR block - "10.20.0.0/16".
- Private subnet - "10.20.1.0/24".
- Private route table.
- No Internet Gateway in this VPC.

VPC Peering

- Peering Connection - "ewb-a-b-peer".
- Requester - "ewb-vpc-a".
- Accepter - "ewb-vpc-b".
- Observed Status – Active.

Routes

Route table| Destination| Target
"ewb-rt-a-public"| "10.20.0.0/16"| VPC peering connection
"ewb-rt-a-private"| "10.20.0.0/16"| VPC peering connection
"ewb-rt-b-private"| "10.10.0.0/16"| VPC peering connection

These routes allow packets destined to another VPC's CIDR block to use VPC peering connection.

Security

Security groups are set up to block SSH and ICMP traffic from certain source addresses. The SSH access to the bastion host must be blocked to all except the administrator's current public IP address.

Testing and Validation

- Status of VPC peering connection: Active.
- Peering routes: Configured.
- SSH connection from the bastion to App A: Troubleshooting pending; connection is timing out.
- Cross-VPC ICMP connectivity: Verification pending.

The results of the testing will be provided once troubleshooting is finished.

Screenshots

Screenshots of VPCs, subnets, VPC peering connection, route tables, security groups, and EC2 instances are attached to the "screenshots/" folder.

Lessons Learned

- VPC CIDR configuration and addressing schemes.
- Setting up the VPC peering connection.
- Configuration of route tables.
- Behavior of security groups and network ACLs.
- Troubleshooting private connectivity.

Cleanup

After the completion of the lab and collection of the necessary evidence, review the AWS resources and delete lab resources to avoid additional charges.