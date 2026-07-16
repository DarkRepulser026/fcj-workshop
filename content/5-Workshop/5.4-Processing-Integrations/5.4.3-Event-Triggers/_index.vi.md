---
title: "5.4.3 Trigger sự kiện"
weight: 3
---

# Trigger sự kiện cho ReviewSentinal

## Tổng quan

Kết nối sự kiện từ storage và database vào các Lambda function để pipeline chạy tự động. Bước này nối hạ tầng đã tạo ở phía trước với business logic ở subpage trước đó.

### Các trigger cần cấu hình

- Sự kiện S3 object-created cho processor Lambda
- Trigger DynamoDB Streams cho analyzer Lambda
- Tùy chọn: lịch EventBridge hằng ngày cho API Lambda

## Từng bước

### 1. Nối trigger S3

1. Mở Lambda `review-sentiment-analyzer-processor`.
2. Chọn **Add trigger**.
3. Chọn **S3**.
4. Chọn bucket upload thô.
5. Đặt event type là **All object create events**.
6. Thêm prefix `uploads/`.
7. Xác nhận cảnh báo recursive invocation và thêm trigger.

### 2. Nối trigger DynamoDB stream

1. Mở Lambda `review-sentiment-analyzer-analyzer`.
2. Chọn **Add trigger**.
3. Chọn **DynamoDB**.
4. Chọn bảng `Reviews`.
5. Giữ batch size `100` và starting position là **Latest**.
6. Thêm filter criteria để chỉ chạy khi `INSERT` và `ProcessingStatus = PENDING`.
7. Bật split batch on error.
8. Thêm trigger.

### 3. Thêm lịch EventBridge tùy chọn

1. Mở Lambda `review-sentiment-analyzer-api`.
2. Chọn **Add trigger**.
3. Chọn **EventBridge (CloudWatch Events)**.
4. Tạo rule mới tên `review-sentiment-analyzer-daily-digest`.
5. Dùng schedule expression `rate(1 day)`.
6. Thêm trigger.

### Ghi chú

1. Trigger S3 mở đầu luồng ingestion.
2. Trigger DynamoDB stream phải lọc để analyzer không tự lặp lại trên bản ghi update của chính nó.
3. EventBridge rule là tùy chọn nhưng nằm trong luồng triển khai đầy đủ.

### Kết quả mong đợi

Luồng xử lý sẽ bắt đầu từ S3, đi qua DynamoDB Streams, và có thể đi vào digest hằng ngày qua EventBridge.
