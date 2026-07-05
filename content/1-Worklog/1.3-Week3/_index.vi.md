---
title: "Worklog Tuần 3"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---
### Mục tiêu Tuần 3:

* Nắm vững các khái niệm cốt lõi của **Amazon EC2**: loại instance, AMI, lưu trữ, bảo mật và các tính năng chính.
* Hiểu các chiến lược tính sẵn sàng cao và các công cụ giám sát cho EC2.
* Phân biệt và áp dụng đúng phương pháp cấp quyền truy cập AWS cho ứng dụng.

### Nhiệm vụ cần thực hiện trong tuần này:

| Chủ đề | Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| EC2 Core Concepts & Cấp quyền | **Amazon EC2 Core Concepts & Cấp quyền Ứng dụng** <br> - Các loại EC2 instance và trường hợp sử dụng phù hợp (Compute/dòng C, Memory/dòng R, General Purpose/dòng T và M) <br> - Amazon Machine Images (AMIs) — AMI do AWS cung cấp, AMI từ Marketplace và AMI tùy chỉnh <br> - Các tùy chọn lưu trữ — EBS volumes (lưu trữ lâu dài) và Instance Store volumes (lưu trữ tạm thời) <br> - Các cơ chế bảo mật — Key pairs, Security Groups, Network ACLs, IAM roles <br> - Các tính năng chính — Auto Scaling, Elastic Load Balancing, VPC networking, Elastic IPs, Placement Groups <br> - Chiến lược tính sẵn sàng cao — Multi-AZ, Local Zones, Outposts, Wavelength Zones <br> - Công cụ giám sát — Amazon CloudWatch, AWS CloudTrail, AWS Systems Manager <br> - Cấp quyền truy cập AWS cho ứng dụng: Access Key/Secret Access Key (và lý do không nên dùng) vs IAM Role trên EC2 (khuyến nghị) | 04/05/2026 | 10/05/2026 | AWS Study Group |

# Thành tựu Tuần 3

## Kiến thức cốt lõi về Amazon EC2
- Nắm rõ các loại EC2 instance (Compute, Memory, General Purpose) và trường hợp sử dụng phù hợp cho từng loại.
- Hiểu về **Amazon Machine Images (AMIs)**: AMI do AWS cung cấp, AMI từ Marketplace và AMI tùy chỉnh.
- Phân biệt các tùy chọn lưu trữ: **EBS volumes** (lâu dài) và **Instance Store volumes** (tạm thời).

## Bảo mật & Tính năng nâng cao
- Tìm hiểu các cơ chế bảo mật: Key pairs, Security Groups, Network ACLs và IAM roles.
- Khám phá các tính năng chính: Auto Scaling, Elastic Load Balancing, VPC networking, Elastic IPs, Placement Groups.
- Nghiên cứu chiến lược tính sẵn sàng cao: Multi-AZ, Local Zones, Outposts, Wavelength Zones.
- Tìm hiểu công cụ giám sát: Amazon CloudWatch, AWS CloudTrail, AWS Systems Manager.

## Quản lý Quyền truy cập cho Ứng dụng
- So sánh việc cấp quyền qua **Access Key/Secret Access Key** và hiểu rõ rủi ro bảo mật khi sử dụng phương pháp này.
- Nắm được lợi ích và cách cấp quyền thông qua **IAM Role** gắn trên EC2 — phương pháp được AWS khuyến nghị.
