---
title: "Week 7 Worklog"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Week 7 Objectives:

* Understand AWS Global Infrastructure and advanced VPC/IP architecture.
* Implement hybrid connectivity with Transit Gateway, Site-to-Site VPN, and Route 53.
* Learn VPC Endpoints, PrivateLink, VPC Peering, and Transit Gateway Network Manager.
* Deploy AWS Managed Microsoft Active Directory and Amazon WorkSpaces.

### Tasks to be carried out this week:

| Topic | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Global Infrastructure & VPC | **Global Infrastructure & VPC Architecture** <br> - AWS Global Infrastructure for Networking: AZs, Regions, Edge Locations <br> - VPC architecture and IP addressing: VPC layout (Non-Production, Production, Shared Resources, Datacenter) and CIDR strategy | 06/01/2026 | 06/07/2026 | AWS Study Group |
| Hybrid Connectivity | **Transit Gateway, VPN & Hybrid DNS** <br> - Transit Gateway and Site-to-Site VPN: a central hub connecting multiple VPCs and on-premises networks <br> - Hybrid DNS with Route 53: Inbound/Outbound Endpoints, Private Hosted Zones, DNS Bind server <br> - VPC Endpoints and PrivateLink: private communication with AWS services, centralized endpoint strategy, VPC Endpoint Services <br> - VPC Peering and Transit Gateway Network Manager: direct connections between two VPCs, global network topology monitoring | 06/01/2026 | 06/07/2026 | AWS Study Group |
| WorkSpaces & Active Directory | **Amazon WorkSpaces & AWS Managed AD** <br> - Amazon WorkSpaces: cloud-based virtual desktops, two connection methods (client app or web browser) <br> - AWS Managed Microsoft Active Directory: a managed Directory Service with high availability, hybrid integration, Standard/Enterprise editions, and group types <br> - Lab infrastructure architecture: EC2 Bastion Host (RDGW), EC2 Windows Server 2022 (AD Manager), AWS Managed Active Directory | 06/01/2026 | 06/07/2026 | AWS Study Group |

# Week 7 Achievements

## Global Infrastructure & VPC Architecture
- Gained a clear understanding of AZs, Regions, and Edge Locations within AWS global infrastructure.
- Designed VPC layouts (Non-Production, Production, Shared Resources, Datacenter) and an appropriate CIDR strategy.

## Advanced Hybrid Connectivity
- Studied **Transit Gateway** and **Site-to-Site VPN** as a central hub connecting multiple VPCs and on-premises networks.
- Configured **Hybrid DNS** with Route 53: Inbound/Outbound Endpoints, Private Hosted Zones, and DNS Bind server.
- Learned **VPC Endpoints/PrivateLink** for private communication with AWS services, and **VPC Peering** combined with Transit Gateway Network Manager to monitor global network topology.

## Virtual Desktops & Active Directory
- Learned about **Amazon WorkSpaces** — cloud-based virtual desktops with two connection methods.
- Deployed **AWS Managed Microsoft Active Directory**: high-availability features, hybrid integration, and Standard/Enterprise editions.
- Built the lab infrastructure: EC2 Bastion Host (RDGW), Windows Server 2022 (AD Manager), AWS Managed AD.
