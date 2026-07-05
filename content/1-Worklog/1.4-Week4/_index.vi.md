---
title: "Worklog Tuần 4"
date: 2026-05-11
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu Tuần 4:

* Làm quen với môi trường phát triển **AWS Cloud9 IDE**.
* Nắm vững các khái niệm cốt lõi của **Amazon S3** và **Amazon RDS**.
* Hiểu sâu về **EC2 Auto Scaling** và **Elastic Load Balancing**.
* Tìm hiểu **Amazon Lightsail** như một giải pháp tối ưu chi phí.

### Nhiệm vụ cần thực hiện trong tuần này:

| Chủ đề | Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| AWS Cloud9 | **AWS Cloud9 IDE** <br> - IDE hoạt động trực tiếp trên trình duyệt web <br> - Soạn thảo code với hỗ trợ đa ngôn ngữ, runtime debugger và terminal tích hợp sẵn <br> - Thao tác cơ bản: thiết lập môi trường, chủ đề màu sắc, phím tắt, tô màu cú pháp | 11/05/2026 | 17/05/2026 | AWS Study Group |
| Amazon S3 | **Amazon S3 Core Concepts** <br> - Buckets và Objects (dữ liệu từ 0 bytes đến 5TB) <br> - Storage class: S3 Standard, Intelligent-Tiering, Standard-IA, Glacier, Glacier Deep Archive <br> - Bảo mật: mã hóa (SSE-S3, SSE-KMS, SSE-C), IAM policies, bucket policies, ACLs <br> - Quản lý: Versioning, Cross-Region Replication, Lifecycle Management, S3 Storage Lens <br> - Use case: Data Lakes, Backup & Restore, Static Website Hosting, lưu trữ dài hạn, Disaster Recovery | 11/05/2026 | 17/05/2026 | AWS Study Group |
| Amazon RDS | **Amazon RDS Core Concepts** <br> - Database engine được hỗ trợ: Aurora, MySQL, MariaDB, Oracle, SQL Server, PostgreSQL <br> - Tùy chọn lưu trữ: General Purpose SSD (gp2/gp3), Provisioned IOPS SSD (io1/io2), Magnetic Storage (legacy) <br> - Tính sẵn sàng cao & DR: Multi-AZ (failover 60–120s), Read Replicas, Global Databases <br> - Bảo mật: mã hóa KMS, VPC, IAM, SSL/TLS <br> - Khả năng mở rộng: dung lượng tối đa 64 TiB <br> - Sao lưu & phục hồi: automated backup với PITR đến 35 ngày, manual snapshot | 11/05/2026 | 17/05/2026 | AWS Study Group |
| Auto Scaling & ELB | **EC2 Auto Scaling & Elastic Load Balancing** <br> - Chiến lược scaling: Manual, Dynamic (Target Tracking, Step, Simple), Scheduled, Predictive <br> - Launch Templates với hỗ trợ versioning <br> - Elastic Load Balancing và Target Groups | 11/05/2026 | 17/05/2026 | AWS Study Group |
| Amazon Lightsail | **Amazon Lightsail** <br> - Triển khai WordPress, PrestaShop, Akaunting bằng OS/Application Blueprints <br> - Cấu hình bảo mật, sao lưu, vertical scaling, cảnh báo giám sát <br> - Lightsail Containers chạy Docker image | 11/05/2026 | 17/05/2026 | AWS Study Group |

# Thành tựu Tuần 4

## Môi trường Phát triển (Cloud9)
- Làm quen với **AWS Cloud9 IDE** — môi trường phát triển tích hợp hoạt động trực tiếp trên trình duyệt, hỗ trợ đa ngôn ngữ, runtime debugger và terminal tích hợp sẵn.

## Lưu trữ Đối tượng (Amazon S3)
- Nắm vững các khái niệm cốt lõi: Buckets, Objects và các storage class (Standard, Intelligent-Tiering, Standard-IA, Glacier, Glacier Deep Archive).
- Hiểu các cơ chế bảo mật (mã hóa SSE-S3/SSE-KMS/SSE-C, IAM/bucket policies, ACLs) và tính năng quản lý (Versioning, CRR, Lifecycle, Storage Lens).
- Tìm hiểu các use case phổ biến: Data Lakes, Backup & Restore, Static Website Hosting, Disaster Recovery.

## Cơ sở dữ liệu Quan hệ (Amazon RDS)
- Nắm rõ các database engine được hỗ trợ và các tùy chọn lưu trữ (gp2/gp3, io1/io2).
- Hiểu chiến lược HA/DR: Multi-AZ, Read Replicas, Global Databases.
- Tìm hiểu cơ chế bảo mật, khả năng mở rộng lưu trữ và chiến lược sao lưu/phục hồi (PITR đến 35 ngày).

## Auto Scaling & Load Balancing
- Nắm vững các chiến lược scaling: Manual, Dynamic (Target Tracking/Step/Simple), Scheduled, Predictive.
- Hiểu vai trò của Launch Templates, Elastic Load Balancing và Target Groups trong kiến trúc có khả năng mở rộng.

## Tối ưu Chi phí với Lightsail
- Triển khai thử nghiệm 3 ứng dụng mã nguồn mở (WordPress, PrestaShop, Akaunting) bằng Lightsail Blueprints.
- Cấu hình bảo mật, sao lưu, vertical scaling và cảnh báo giám sát cho từng ứng dụng.
- Tìm hiểu Lightsail Containers để chạy ứng dụng đóng gói bằng Docker.
