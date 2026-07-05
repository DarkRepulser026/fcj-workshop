---
title: "Worklog Tuần 6"
date: 2026-05-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu Tuần 6:

* Nắm vững các khái niệm cốt lõi và thao tác quản lý **Amazon DynamoDB**.
* Tìm hiểu và triển khai **Amazon ElastiCache for Redis**.

### Nhiệm vụ cần thực hiện trong tuần này:

| Chủ đề | Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| Amazon DynamoDB | **DynamoDB Core Concepts** <br> - DynamoDB là dịch vụ cơ sở dữ liệu NoSQL được quản lý hoàn toàn với hiệu suất nhanh, dự đoán được, khả năng mở rộng liền mạch và mã hóa lưu trữ <br> - Thành phần cốt lõi: tables, primary keys (partition key và composite key), secondary indexes (Global và Local), kiểu dữ liệu, mô hình read consistency <br> - Chế độ Read/Write Capacity: on-demand và provisioned <br> - Sao lưu & phục hồi: on-demand backup, point-in-time recovery đến 35 ngày, TTL <br> - Quản lý qua Console (tạo table, CRUD, GSI), qua CloudShell (CLI) và qua AWS SDK/Python Boto3 | 25/05/2026 | 31/05/2026 | AWS Study Group |
| Amazon ElastiCache | **ElastiCache for Redis** <br> - Dịch vụ in-memory caching được quản lý hoàn toàn với tự động phát hiện lỗi, phục hồi, sao lưu và vá lỗi <br> - Thành phần cốt lõi: clusters, nodes, shards (tối đa 500 shards khi bật cluster mode) <br> - Chế độ cluster: Cluster Mode Disabled và Cluster Mode Enabled <br> - Loại lưu trữ node: Standard và memory-optimized, triển khai trong VPC <br> - Tạo cluster qua Console và CLI: subnet groups, cluster mode, cấp quyền và kết nối <br> - Sử dụng AWS SDK: tạo cluster, kết nối, Set/Get, hash, publish/subscribe, stream read/write | 25/05/2026 | 31/05/2026 | AWS Study Group |

# Thành tựu Tuần 6

## Cơ sở dữ liệu NoSQL (DynamoDB)
- Nắm rõ các thành phần cốt lõi: tables, primary keys, secondary indexes (GSI/LSI), kiểu dữ liệu và read consistency.
- Hiểu sự khác biệt giữa chế độ On-Demand và Provisioned Capacity.
- Thực hành CRUD, tạo và truy vấn GSI qua Console, CloudShell và AWS SDK (Python/Boto3).
- Tìm hiểu cơ chế sao lưu/phục hồi: on-demand backup, PITR (35 ngày), TTL.

## Bộ nhớ đệm (ElastiCache for Redis)
- Hiểu các thành phần cốt lõi: clusters, nodes, shards (tối đa 500 shards khi bật cluster mode).
- Phân biệt Cluster Mode Enabled/Disabled và các loại node lưu trữ.
- Thực hành tạo cluster qua Console và CLI (subnet groups, quyền, kết nối).
- Sử dụng AWS SDK để thao tác Set/Get, hash, publish/subscribe và stream read/write.
