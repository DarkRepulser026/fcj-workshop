---
title: "Worklog Tuần 2"
date: 2026-04-27
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---
### Mục tiêu Tuần 2:

* Phân biệt và áp dụng đúng các cơ chế bảo mật mạng trong VPC: Security Groups và Network ACLs.
* Triển khai hạ tầng VPC hoàn chỉnh với Subnet đa AZ, Internet Gateway, Route Table và VPC Flow Logs.
* Triển khai và kiểm tra kết nối EC2 instances thông qua SSH và AWS Systems Manager Session Manager.

### Nhiệm vụ cần thực hiện trong tuần này:

| Chủ đề | Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| VPC Security & Hạ tầng mạng | **VPC Security Controls & Hạ tầng EC2** <br> - Tìm hiểu VPC Security Controls: Security Groups (stateful, cấp instance) và NACLs (stateless, cấp subnet), so sánh sự khác biệt <br> - Thực hành **VPC Preparation Workshop**: tạo VPC, Subnet đa AZ (public & private), Internet Gateway, Route Table, Security Group, bật VPC Flow Logs <br> - Triển khai hạ tầng EC2: tạo EC2 Instances, kiểm tra kết nối SSH và AWS Systems Manager Session Manager, tạo NAT Gateway đa AZ, sử dụng VPC Reachability Analyzer | 27/04/2026 | 03/05/2026 | AWS Study Group |

# Thành tựu Tuần 2

## Bảo mật Mạng trong VPC
- So sánh và nắm rõ sự khác biệt giữa **Security Groups** (stateful, hoạt động ở cấp instance) và **Network ACLs** (stateless, hoạt động ở cấp subnet).

## Triển khai Hạ tầng VPC
- Hoàn thành **VPC Preparation Workshop**: tạo VPC, Subnet đa AZ (public & private), Internet Gateway, Route Table, Security Group.
- Bật **VPC Flow Logs** để giám sát lưu lượng mạng.

## Triển khai & Kiểm tra EC2
- Triển khai **EC2 Instances** và kiểm tra kết nối qua **SSH** và **AWS Systems Manager Session Manager**.
- Cấu hình **NAT Gateway đa AZ** để đảm bảo tính sẵn sàng cao cho kết nối outbound.
- Sử dụng **VPC Reachability Analyzer** để chẩn đoán kết nối mạng.
