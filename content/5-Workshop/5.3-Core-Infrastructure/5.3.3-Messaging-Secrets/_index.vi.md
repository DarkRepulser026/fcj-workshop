---
title: "5.03.3 Messaging và secret"
weight: 3
---

# Messaging và secret cho ReviewSentinal

## Tổng quan

Tạo dead-letter queue, SNS topic cảnh báo, và secret tùy chọn mà các Lambda sẽ dùng ở các bước sau.

### SQS dead-letter queue

1. Mở SQS và chọn **Create queue**.
2. Chọn **Standard**.
3. Đặt tên queue là `lambda-dlq`.
4. Xác nhận encryption **SSE-SQS** đang bật.
5. Đặt message retention là 14 ngày.
6. Tạo queue.
7. Copy ARN của queue từ trang chi tiết.

### SNS alert topic

1. Mở SNS và vào **Topics** → **Create topic**.
2. Chọn **Standard**.
3. Đặt tên topic là `sentiment-alerts`.
4. Giữ encryption bằng key AWS managed mặc định của SNS.
5. Tạo topic.
6. Tạo email subscription bằng chính email của bạn.
7. Xác nhận subscription từ inbox.
8. Copy ARN của topic.

### Secrets Manager secret

1. Mở Secrets Manager và chọn **Store a new secret**.
2. Chọn **Other type of secret**.
3. Dùng tab **Plaintext**, không dùng key/value pairs.
4. Nhập giá trị placeholder như `REPLACE_ME_LATER`.
5. Giữ encryption bằng key AWS-managed mặc định.
6. Đặt tên secret `review-sentiment-analyzer-openrouter-api-key`.
7. Bỏ rotation và lưu lại.
8. Copy ARN của secret.

### Ghi chú

- Giữ secret dạng plain text vì Lambda đọc raw string trực tiếp.
- DLQ được các Lambda dùng cho xử lý lỗi bất đồng bộ.
- Ở bước kế tiếp bạn sẽ paste các ARN này vào IAM policy.

### Kết quả mong đợi

Bạn phải có ARN của SQS DLQ, ARN của SNS topic với subscription email đã xác nhận, và ARN của Secrets Manager secret để dùng cho IAM role.
