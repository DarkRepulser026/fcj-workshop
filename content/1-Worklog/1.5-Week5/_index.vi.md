---
title: "Worklog Tuần 5"
date: 2026-05-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu Tuần 5:

* Triển khai giám sát và observability toàn diện với **Amazon CloudWatch**.
* Thiết lập **Hybrid DNS** với Route 53 Resolver.
* Thành thạo cấu hình và sử dụng **AWS CLI**.

### Nhiệm vụ cần thực hiện trong tuần này:

| Chủ đề | Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| Amazon CloudWatch | **Monitoring & Observability** <br> - CloudWatch là dịch vụ giám sát thống nhất thu thập metrics, logs và events trên toàn bộ tài nguyên AWS, hybrid và on-premises <br> - Các tính năng chính: metrics độ phân giải cao (1 giây), lưu trữ dữ liệu 15 tháng, tự động hóa hành động dựa trên cảnh báo, observability end-to-end để giảm MTTR <br> - Làm việc với Metrics từ ứng dụng mẫu trên EC2, xem/tạo custom Metrics từ Logs, cấu hình Alarms, xây dựng Dashboard tùy chỉnh | 18/05/2026 | 24/05/2026 | AWS Study Group |
| Route 53 Resolver | **Hybrid DNS** <br> - Các tính năng DNS của Route 53: đăng ký public domain, private DNS zones, hybrid DNS engine, phân giải tên miền <br> - Outbound Endpoints: chuyển tiếp DNS query từ AWS đến hệ thống DNS on-premises <br> - Inbound Endpoints: nhận DNS query từ hệ thống on-premises hướng đến domain trên AWS <br> - Resolver Rules: cấu hình chuyển tiếp DNS query cho các domain cụ thể | 18/05/2026 | 24/05/2026 | AWS Study Group |
| AWS CLI | **AWS Command Line Interface** <br> - CLI là công cụ mã nguồn mở để tương tác và tự động hóa dịch vụ AWS qua dòng lệnh <br> - CLI Profiles: profile mặc định và profile được đặt tên <br> - Cấu hình CLI qua `aws configure`: Access Key ID, Secret Access Key, region mặc định, định dạng output <br> - Các định dạng output: json (mặc định), yaml, yaml-stream, text, table | 18/05/2026 | 24/05/2026 | AWS Study Group |

# Thành tựu Tuần 5

## Giám sát & Observability (CloudWatch)
- Hiểu CloudWatch là dịch vụ giám sát thống nhất, thu thập metrics/logs/events trên toàn bộ tài nguyên AWS, hybrid và on-premises.
- Thực hành làm việc với Metrics, custom Metrics từ Logs, cấu hình Alarms và xây dựng Dashboard tùy chỉnh.

## Hybrid DNS (Route 53 Resolver)
- Tìm hiểu Outbound Endpoints (chuyển tiếp query từ AWS ra on-prem) và Inbound Endpoints (nhận query từ on-prem vào AWS).
- Cấu hình Resolver Rules để định tuyến DNS query cho các domain cụ thể.

## AWS CLI
- Nắm rõ khái niệm CLI Profiles (mặc định và có tên) để quản lý nhiều môi trường AWS.
- Thực hành cấu hình CLI qua `aws configure` và các định dạng output: json, yaml, yaml-stream, text, table.
