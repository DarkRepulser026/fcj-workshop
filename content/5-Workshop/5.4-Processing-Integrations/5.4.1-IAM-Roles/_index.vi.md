---
title: "5.4.1 IAM role"
weight: 1
---

# IAM role cho lớp xử lý

## Tổng quan

Tạo một IAM role tối thiểu quyền cho từng Lambda function của ReviewSentinal. Không nên dùng chung một role: processor, analyzer và API handler truy cập các nhóm tài nguyên khác nhau.

### Các role cần tạo

- `review-processor-role`
- `sentiment-analyzer-role`
- `api-handler-role`

### Yêu cầu chung

- Trust policy: `lambda.amazonaws.com`
- Quyền CloudWatch Logs cho cả ba role
- Quyền gửi SQS cho DLQ
- Quyền S3, DynamoDB, SNS và Secrets Manager được giới hạn theo từng Lambda function

## Từng bước

### 1. Tạo role cho processor

1. Mở IAM console và vào **Roles**.
2. Chọn **Create role**.
3. Chọn **AWS service** làm trusted entity.
4. Chọn use case **Lambda**.
5. Không attach managed policy nào ở bước này.
6. Đặt tên role là `review-processor-role` rồi tạo role.
7. Mở role và tạo inline policy trong tab **JSON**.
8. Dán policy của processor từ hướng dẫn triển khai và thay `<ACCOUNT_ID>` bằng account ID thật.
9. Lưu policy với tên `review-processor-policy`.

### 2. Tạo role cho sentiment analyzer

1. Lặp lại flow tạo role.
2. Đặt tên role là `sentiment-analyzer-role`.
3. Tạo inline policy thứ hai tên `sentiment-analyzer-policy`.
4. Dán policy của analyzer từ hướng dẫn triển khai.
5. Thay `<ACCOUNT_ID>` và ARN của Secrets Manager bằng giá trị thật.
6. Đảm bảo statement `DynamoDBStreamsAccess` vẫn có mặt.

### 3. Tạo role cho API handler

1. Tạo role Lambda thứ ba.
2. Đặt tên là `api-handler-role`.
3. Gắn inline policy `api-handler-policy`.
4. Dán policy đầy đủ từ hướng dẫn triển khai.
5. Thay `<ACCOUNT_ID>` và secret ARN bằng giá trị thật.

### Ghi chú

1. Processor cần quyền đọc S3 và ghi DynamoDB.
2. Analyzer cần quyền stream ngoài quyền truy cập bảng.
3. API handler cần quyền bảng rộng hơn vì phục vụ REST API và daily digest.
4. Giữ CloudWatch Logs permissions trong cả ba role để function ghi log ngay từ lần chạy đầu.

### Kết quả mong đợi

Kết thúc bước này, bạn sẽ có ba IAM role sẵn sàng để gắn vào các Lambda function ở subpage tiếp theo.
