---
title: "Worklog Tuần 11"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục Tiêu Tuần 11
* Hoàn thiện kiến trúc tổng thể của hệ thống ReviewSentinel (lớp edge, application, xử lý, phân tích, giám sát).
* Xác định mô hình bảo mật: luồng xác thực Cognito, phân quyền IAM theo nguyên tắc tối thiểu, phân quyền API Gateway.
* Thiết kế mô hình dữ liệu DynamoDB (bảng Reviews, Products, Users và các mẫu truy vấn).
* Soạn thảo đặc tả các Lambda function (review-processor, sentiment-analyzer, API handler) và trigger tương ứng.
* Chuẩn bị phương pháp triển khai hạ tầng và môi trường dev/test cục bộ.
* Chuẩn bị thành phần hạ tầng nền tảng (S3 bucket, bảng DynamoDB) để triển khai.

---

### Các Công Việc Thực Hiện Trong Tuần

| Ngày | Công Việc | Ngày Bắt Đầu | Ngày Hoàn Thành | Tài Liệu Tham Khảo |
|-----|------|-------------|------------------|--------------------|
| 2 | Rà soát và hoàn thiện sơ đồ kiến trúc ReviewSentinel (các lớp edge/app/processing/analytics). <br>- Xác nhận lựa chọn dịch vụ AWS và luồng dữ liệu. | 29/06/2026 | 29/06/2026 | AWS Study Group |
| 3 | Thiết kế mô hình bảo mật: Cognito user pool, authorizer API Gateway dựa trên JWT, phân quyền IAM. <br>- Ghi nhận các rủi ro bảo mật cần lưu ý đối với dự án ở quy mô demo. | 30/06/2026 | 30/06/2026 | AWS Study Group |
| 4 | Thiết kế schema DynamoDB (Reviews, Products, Users) gồm khóa chính, GSI và các mẫu truy cập dữ liệu. <br>- Lên kế hoạch bố trí S3 bucket và event trigger. | 01/07/2026 | 01/07/2026 | AWS Study Group |
| 5 | Soạn thảo đặc tả Lambda function: `review_processor`, `sentiment_analyzer`, `api_handler`. <br>- Xác định input/output và cách xử lý lỗi thống nhất. | 02/07/2026 | 02/07/2026 | AWS Study Group |
| 6 | Chuẩn bị phương pháp triển khai hạ tầng và môi trường phát triển.<br>- Chuẩn bị thành phần hạ tầng nền tảng (S3 bucket, bảng DynamoDB). | 03/07/2026 | 03/07/2026 | AWS Study Group |

---

### Kết Quả Đạt Được Tuần 11

#### **1. Hoàn Thiện Kiến Trúc Hệ Thống**
Tôi đã rà soát và chốt kiến trúc ReviewSentinel (v5), bao gồm lớp edge/bảo mật, lớp ứng dụng (API Gateway, Cognito, API Lambda), lớp xử lý (Lambda kích hoạt bởi S3 và DynamoDB Stream), và lớp phân tích (Comprehend, Bedrock). Vì đây là dự án học tập/demo, tôi chủ động giữ thiết kế đơn giản, không đầu tư quá mức cho khả năng mở rộng, mà ưu tiên tính rõ ràng và đúng đắn của chức năng.

#### **2. Thiết Kế Mô Hình Bảo Mật**
Tôi đã lên kế hoạch cho luồng xác thực và phân quyền: Cognito User Pool cho đăng ký/đăng nhập, token JWT được xác thực qua Lambda authorizer của API Gateway, và các IAM role được giới hạn quyền tối thiểu cho từng Lambda function. Tôi cũng ghi lại các nguyên tắc bảo mật cơ bản cần áp dụng sau này — không để S3 bucket công khai, mã hóa dữ liệu tại DynamoDB, và không ghi dữ liệu nhạy cảm vào log.

#### **3. Thiết Kế Mô Hình Dữ Liệu**
Tôi đã xác định cấu trúc bảng DynamoDB cho Reviews, Products và Users, bao gồm khóa chính và các GSI cần thiết để phục vụ các mẫu truy vấn đã lên kế hoạch (ví dụ: review theo sản phẩm, thống kê theo khoảng thời gian). Tôi cũng đã phác thảo cách bố trí S3 bucket cho việc upload review thô và các event notification sẽ kích hoạt xử lý ở bước tiếp theo.

#### **4. Soạn Thảo Đặc Tả Lambda Function**
Tôi đã viết đặc tả cho ba Lambda function chính — `review_processor` (kích hoạt bởi S3, xử lý validate/làm sạch/loại trùng dữ liệu), `sentiment_analyzer` (kích hoạt bởi DynamoDB Streams, phân tích qua Comprehend và tùy chọn Bedrock), và `api_handler` (các endpoint REST của API Gateway). Mỗi đặc tả đều nêu rõ input/output mong đợi và định dạng xử lý lỗi/phản hồi thống nhất nhằm giảm thiểu vấn đề khi tích hợp ở giai đoạn triển khai.

#### **5. Chuẩn Bị Phương Pháp Triển Khai Hạ Tầng Và Môi Trường Phát Triển**
Tôi đã xác định phương pháp triển khai hạ tầng và chuẩn bị môi trường phát triển. Tôi đã hoàn thiện các specification cho các thành phần hạ tầng nền tảng (S3 bucket và bảng DynamoDB) để Tuần 12 có thể tập trung vào việc triển khai logique ứng dụng mà không cần phải lên kế hoạch lại phần hạ tầng cơ bản.

#### **6. Đặt Nền Tảng Cho Tuần 12**
Sau khi hoàn thiện kiến trúc, mô hình bảo mật, mô hình dữ liệu và đặc tả Lambda, cùng với việc đã chuẩn bị xong các thành phần hạ tầng nền tảng, dự án đã sẵn sàng bước vào giai đoạn triển khai đầy đủ trong tuần tới: deploy các Lambda function, kết nối API Gateway với phân quyền Cognito, tích hợp frontend React, và kiểm thử toàn bộ luồng end-to-end cùng với giám sát qua CloudWatch.

---