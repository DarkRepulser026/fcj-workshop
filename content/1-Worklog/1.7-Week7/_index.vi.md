---
title: "Worklog Tuần 7"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Mục tiêu Tuần 7:

* Hiểu Hạ tầng Toàn cầu AWS và kiến trúc VPC/IP nâng cao.
* Triển khai kết nối hybrid với Transit Gateway, Site-to-Site VPN và Route 53.
* Tìm hiểu VPC Endpoints, PrivateLink, VPC Peering và Transit Gateway Network Manager.
* Triển khai AWS Managed Microsoft Active Directory và Amazon WorkSpaces.

### Nhiệm vụ cần thực hiện trong tuần này:

| Chủ đề | Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| Hạ tầng Toàn cầu & VPC | **Hạ tầng Toàn cầu & Kiến trúc VPC** <br> - Hạ tầng Toàn cầu AWS cho Networking: AZs, Regions, Edge Locations <br> - Kiến trúc VPC và Địa chỉ IP: bố cục VPC (Non-Production, Production, Shared Resources, Datacenter) và chiến lược CIDR | 01/06/2026 | 07/06/2026 | AWS Study Group |
| Kết nối Hybrid | **Transit Gateway, VPN & Hybrid DNS** <br> - Transit Gateway và Site-to-Site VPN: hub trung tâm kết nối nhiều VPC và mạng on-premises <br> - Hybrid DNS với Route 53: Inbound/Outbound Endpoints, Private Hosted Zones, DNS Bind server <br> - VPC Endpoints và PrivateLink: giao tiếp riêng tư với dịch vụ AWS, chiến lược endpoint tập trung, VPC Endpoint Services <br> - VPC Peering và Transit Gateway Network Manager: kết nối trực tiếp giữa hai VPC, giám sát topology mạng toàn cầu | 01/06/2026 | 07/06/2026 | AWS Study Group |
| WorkSpaces & Active Directory | **Amazon WorkSpaces & AWS Managed AD** <br> - Amazon WorkSpaces: máy tính để bàn ảo trên cloud, hai phương thức kết nối (client app hoặc trình duyệt web) <br> - AWS Managed Microsoft Active Directory: dịch vụ Directory Service được quản lý, High Availability, tích hợp hybrid, phiên bản Standard/Enterprise, các loại Group <br> - Kiến trúc Hạ tầng Lab: EC2 Bastion Host (RDGW), EC2 Windows Server 2022 (AD Manager), AWS Managed Active Directory | 01/06/2026 | 07/06/2026 | AWS Study Group |

# Thành tựu Tuần 7

## Hạ tầng Toàn cầu & Kiến trúc VPC
- Nắm rõ các khái niệm AZs, Regions, Edge Locations trong hạ tầng toàn cầu AWS.
- Thiết kế bố cục VPC (Non-Production, Production, Shared Resources, Datacenter) và chiến lược CIDR phù hợp.

## Kết nối Hybrid nâng cao
- Tìm hiểu **Transit Gateway** và **Site-to-Site VPN** làm hub trung tâm kết nối nhiều VPC và mạng on-premises.
- Cấu hình **Hybrid DNS** với Route 53: Inbound/Outbound Endpoints, Private Hosted Zones, DNS Bind server.
- Tìm hiểu **VPC Endpoints/PrivateLink** cho giao tiếp riêng tư với dịch vụ AWS, và **VPC Peering** kết hợp Transit Gateway Network Manager để giám sát topology mạng toàn cầu.

## Ảo hóa & Active Directory
- Tìm hiểu **Amazon WorkSpaces** — máy tính để bàn ảo trên cloud với hai phương thức kết nối.
- Triển khai **AWS Managed Microsoft Active Directory**: tính năng High Availability, tích hợp hybrid, các phiên bản Standard/Enterprise.
- Xây dựng hạ tầng lab: EC2 Bastion Host (RDGW), Windows Server 2022 (AD Manager), AWS Managed AD.
