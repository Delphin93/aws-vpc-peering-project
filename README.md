# AWS VPC Peering Project

## Project Overview
This project demonstrates how to establish private network connectivity between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering.
The project uses separate VPCs, private subnets, route tables, security groups, and EC2 instances to test communication through private IP addresses.

## Objectives

- Create and configure two VPCs with non-overlapping CIDR ranges.
- Configure public and private subnets.
- Create and activate a VPC peering connection.
- Configure route tables for communication between the VPCs.
- Configure security groups to allow required SSH and ICMP traffic.
- Verify connectivity between private EC2 instances.

## Architecture

### VPC A
- **VPC Name:** `ewb-vpc-a`
- **CIDR:** `10.10.0.0/16`
- **Public Subnet:** `ewb-a-public` — `10.10.1.0/24`
- **Private Subnet:** `ewb-a-private` — `10.10.2.0/24`
- **Bastion Host Private IP:** `10.10.1.75`
- **App-A Private IP:** `10.10.2.84`

### VPC B
- **VPC Name:** `ewb-vpc-b`
- **CIDR:** `10.20.0.0/16`
- **Private Subnet:** `ewb-b-private` — `10.20.1.0/24`
- **App-B Private IP:** `10.20.1.72`

### VPC Peering
- **Connection Name:** `ewb-a-b-peer`
- **Status:** Active
- **Purpose:** Enable private communication between VPC A and VPC B.

  
## Implementation Steps

1. Created VPC A and VPC B with non-overlapping CIDR ranges.
2. Created the required public and private subnets.
3. Attached an Internet Gateway to VPC A.
4. Configured route tables for public and private subnets.
5. Created security groups for the Bastion Host, App-A, and App-B.
6. Launched three EC2 instances using Amazon Linux 2023.
7. Created and activated the VPC peering connection.
8. Added routes for the remote VPC CIDR ranges through the peering connection.
9. Configured SSH access to private instances through the Bastion Host.
10. Tested connectivity between App-A and App-B using ICMP ping.

## Testing and Results

### Test 1: App-A to App-B

- **Source:** App-A — `10.10.2.84`
- **Destination:** App-B — `10.20.1.72`
- **Result:** Successful
- **Packets received:** 4 out of 4
- **Packet loss:** 0%

### Test 2: App-B to App-A

- **Source:** App-B — `10.20.1.72`
- **Destination:** App-A — `10.10.2.84`
- **Result:** Successful
- **Packets received:** 4 out of 4
- **Packet loss:** 0%

Both tests confirmed private connectivity between the two VPCs through the active peering connection.

## Key Learnings

- VPC CIDR planning and subnet configuration.
- Route table configuration and traffic routing.
- Security group rules for SSH and ICMP.
- Secure access to private EC2 instances through a Bastion Host.
- Private communication between VPCs using VPC Peering.
- Connectivity testing and troubleshooting.

- ## Technologies Used

- Amazon Web Services (AWS)
- Amazon VPC
- VPC Peering
- Amazon EC2
- Route Tables
- Security Groups
- Internet Gateway
- Amazon Linux 2023
- SSH and ICMP

- ## Project Status

The VPC peering connection is active, and bidirectional connectivity tests have passed. Evidence screenshots and final cleanup are pending.

## Security Note

No private SSH keys, passwords, or AWS access credentials should be stored in this repository.







