---
title: "Hạ tầng nền"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### Tổng quan

Phần này tạo lớp nền dùng chung cho ReviewSentinal: S3 để upload review thô, DynamoDB để lưu review và sản phẩm, SNS để gửi cảnh báo, SQS để giữ sự kiện lỗi, và Secrets Manager cho API key OpenRouter tùy chọn.

#### Nội dung

1. [S3 buckets](5.03.1-s3-buckets/)
2. [DynamoDB tables](5.03.2-dynamodb-tables/)
3. [Messaging và secret](5.03.3-messaging-secrets/)

#### Xây dựng hạ tầng nền

1. Tạo bucket S3 cho file tải lên thô và giữ chặn truy cập công khai.
2. Tạo ba bảng DynamoDB: `Reviews`, `Products` và `Users`.
3. Bật DynamoDB Streams và point-in-time recovery cho bảng `Reviews`.
4. Tạo SNS topic cho cảnh báo review tiêu cực và SQS dead-letter queue.
5. Lưu placeholder API key OpenRouter trong Secrets Manager nếu bạn muốn bật bước phân tích sâu hơn sau này.

#### Ghi chú

+ Dùng cùng region và cùng kiểu đặt tên ở mọi nơi để Lambda role có thể tham chiếu ARN một cách dễ đoán.
+ Bucket upload cần cấu hình CORS để browser có thể upload trực tiếp.
+ Giữ tên tài nguyên khớp đúng với hướng dẫn triển khai, vì các phần sau sẽ đưa chúng vào IAM policy và biến môi trường.
