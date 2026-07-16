---
title: "5.6.2 Dọn dẹp backend và dữ liệu"
weight: 2
---

# Dọn dẹp backend và dữ liệu

## Tổng quan

Xóa các tài nguyên API, compute, storage, messaging và secret đang vận hành ứng dụng.

### Những gì cần xóa

- Stage API Gateway và REST API
- Lambda function và IAM role
- Bucket S3 dùng để upload
- Các bảng DynamoDB
- SNS topic và SQS queue
- Secrets Manager secret
- CloudWatch dashboard và alarm

## Từng bước

1. Xóa API Gateway API và stage của nó.
2. Xóa API key và usage plan của webhook nếu đã tạo.
3. Xóa EventBridge rule digest.
4. Xóa ba Lambda function.
5. Xóa CloudWatch log groups của các function đó.
6. Xóa IAM role mà Lambda đang dùng.
7. Xóa SQS queue và SNS topic.
8. Xóa Secrets Manager secret.
9. Xóa các bảng DynamoDB.
10. Làm rỗng rồi xóa bucket S3 upload.
11. Xóa CloudWatch dashboard và alarm.

## Ghi chú

1. Xóa Lambda function trước rồi mới xóa role mà chúng dùng.
2. Làm rỗng bucket S3 trước khi xóa bucket.
3. Giữ thứ tự đơn giản để các tài nguyên phụ thuộc biến mất sạch sẽ.

## Kết quả mong đợi

Sau bước này, các dịch vụ chính của ứng dụng không còn tồn tại.
