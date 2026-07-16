---
title: "5.3.2 DynamoDB tables"
weight: 2
---

# Các bảng DynamoDB cho ReviewSentinal

## Tổng quan

Tạo ba bảng lưu review, sản phẩm và người dùng. Bảng `Reviews` là bảng chính và cần stream cùng GSI.

### Các bảng cần tạo

- `Reviews`
- `Products`
- `Users`

### Bảng Reviews

1. Mở DynamoDB và chọn **Create table**.
2. Table name: `Reviews`.
3. Partition key: `ProductID` kiểu String.
4. Sort key: `ReviewID` kiểu String.
5. Chọn **Customize**.
6. Đặt capacity là **On-demand**.
7. Để encryption theo key do DynamoDB quản lý mặc định.
8. Tạo bảng.

Sau khi tạo xong:

1. Mở bảng `Reviews`.
2. Bật **DynamoDB Streams** ở tab **Exports and streams**.
3. Chọn stream view type là **New image**.
4. Vào tab **Backups** và bật **Point-in-time recovery**.
5. Tạo GSI tên `SentimentIndex`.
6. Dùng `ProductID` làm partition key và `Sentiment` làm sort key.
7. Chỉ project các thuộc tính `ReviewText`, `Rating`, `CreatedAt`, `KeyPhrases`, và `UserID`.

### Bảng Products

1. Tạo bảng tên `Products`.
2. Dùng `ProductID` làm partition key.
3. Không dùng sort key.
4. Chọn **On-demand**.
5. Bật point-in-time recovery sau khi tạo.

### Bảng Users

1. Tạo bảng tên `Users`.
2. Dùng `UserID` làm partition key.
3. Không dùng sort key.
4. Chọn **On-demand**.
5. Bật point-in-time recovery sau khi tạo.

### Ghi chú

- Stream của bảng `Reviews` cần cho trigger của Lambda sentiment analyzer.
- Giữ đúng tên bảng vì biến môi trường và IAM policy phía sau sẽ tham chiếu trực tiếp.
- GSI được giữ tối giản để chỉ trả chi phí cho những gì code thực sự dùng.

### Kết quả mong đợi

Ba bảng phải tồn tại, `Reviews` phải bật streams, và tất cả bảng phải là on-demand với point-in-time recovery.
