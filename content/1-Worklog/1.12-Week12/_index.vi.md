---
title: "Nhật ký Công việc Tuần 12"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu Tuần 12:

* Hoàn thành việc triển khai từ đầu đến cuối của dự án workshop ReviewSentinal
* Triển khai tất cả hạ tầng, dịch vụ backend và tích hợp frontend
* Xác thực pipeline hoàn chỉnh bằng dữ liệu test mẫu
* Chuẩn bị cho dọn dẹp và tài liệu

### Công việc cần thực hiện trong tuần này:
| Ngày | Công việc                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                        |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2    | - Triển khai các hàm Lambda: review_processor, sentiment_analyzer, api_handler<br>- Cấu hình vai trò IAM với chính sách ít nhất quyền<br>- Triển khai các hàm Lambda với xử lý và biến môi trường chính xác | 08/07/2026 | 10/07/2026      | AWS Study Group                           |
| 3    | - Cấu hình API Gateway với authorizer Cognito<br>- Bật CORS trên tất cả tài nguyên công cộng<br>- Triển khai REST API lên giai đoạn dev<br>- Cấp quyền gọi Lambda từ API Gateway                                       | 11/07/2026 | 12/07/2026      | AWS Study Group                           |
| 4    | - Thiết lập thông báo S3 bucket để kích hoạt Lambda review_processor<br>- Cấu hình trigger DynamoDB Streams cho Lambda sentiment_analyzer<br>- Thêm tiêu chí lọc cho sự kiện INSERT có trạng thái PENDING     | 13/07/2026 | 14/07/2026      | AWS Study Group                           |
| 5    | - Xây dựng và cấu hình frontend React TypeScript Vite<br>- Đặt biến môi trường (URL API, cài đặt Cognito)<br>- Triển khai frontend lên Amplify<br>- Cập nhật URL callback/sign-out của Cognito và CORS S3      | 15/07/2026 | 16/07/2026      | AWS Study Group                           |
| 6    | - Chạy xác thực từ đầu đến cuối: đăng ký Cognito, tải lên file, xử lý pipeline<br>- Xác minh bảng điều khiển CloudWatch hiển thị chỉ số khỏe mạnh<br>- Kiểm tra đường dẫn OpenRouter tùy chọn nếu có sẵn API key | 17/07/2026 | 18/07/2026      | AWS Study Group                           |

### Thành tựu Tuần 12:

* **Đã triển khai thành công ba hàm Lambda** với vai trò IAM thích hợp:
  - `review_processor`: Xác thực việc upload S3, ghi bản ghi review ban đầu vào DynamoDB
  - `sentiment_analyzer`: Xử lý luồng DynamoDB Streams, sử dụng Comprehend để phân tích cảm xúc, tùy chọn gọi OpenRouter, gửi email hoàn thành qua Amazon SES
  - `api_handler`: Cung cấp các điểm cuối API REST cho các endpoint về sản phẩm, đánh giá, upload và phân tích

* **Đã cấu hình kiến trúc kiến trúc dựa trên sự kiện hoàn chỉnh**:
  - Các sự kiện tạo đối tượng S3 kích hoạt Lambda review_processor (có bộ lọc tiền tố uploads/)
  - DynamoDB Streams trên bảng Reviews kích hoạt Lambda sentiment_analyzer (lọc cho các sự kiện INSERT có ProcessingStatus=PENDING)
  - Xử lý lỗi thích hợp được cấu hình với DLQ (lambda-dlq) cho tất cả

* **Đã triển khai hoàn toàn API Gateway**:
  - API REST với authorizer Cognito bảo vệ tất cả các endpoint
  - CORS được cấu hình trên tất cả các tài nguyên công cộng (cho phép Content-Type, Authorization, X-Api-Key, X-Amz-Security-Token)
  - Giai đoạn dev được triển khai với URL Invoke có thể truy cập được
  - Quyền gọi Lambda được cấp đúng cách từ API Gateway

* **Đã triển khai tích hợp frontend hoàn chỉnh**:
  - Xây dựng ứng dụng React TypeScript Vite với CSS theo dõi Tailwind
  - Định cấu hình các biến môi trường trỏ đến tài nguyên API Gateway và Cognito đã triển khai
  - Thành công triển khai lên AWS Amplify với miền tùy chỉnh
  - Cập nhật URL callback/sign-out của Cognito User Pool và CORS origins được phép của bucket S3 để bao gồm miền frontend

* **Đã xác thực đầy đủ chức năng pipeline từ đầu đến cuối**:
  - Đăng ký và đăng nhập thành công qua Cognito Hosted UI
  - Tải lên các file review mẫu qua giao diện trình duyệt
  - Xác minh Lambda processor đã ghi bản ghi ban đầu vào bảng DynamoDB Reviews
  - Xác minh Lambda analyzer đã xử lý luồng, cập nhật bản ghi bằng kết quả phân tích cảm xúc, và gửi email hoàn thành qua SES
  - Xác minh bảng điều khiển CloudWatch hiển thị chỉ số gọi và lỗi khỏe mạnh
  - Kiểm tra đường dẫn OpenRouter tùy chọn bằng cách lưu trữ API key trong Secrets Manager và bật phân tích sâu

* **Đã triển khai khả năng quan sát toàn diện**:
  - Tạo bảng điều khiển CloudWatch hiển thị chỉ số gọi, lỗi và thời lượng của các hàm Lambda
  - Định cấu hình cảnh báo lỗi Lambda (5+ lỗi trong cửa sổ 5 phút) gửi thông báo qua SES
  - Đặt báo hiệu độ trễ API (>5000ms thời gian trễ) để gửi thông báo qua SES
  - Thiết lập cảnh báo ngân sách hàng tháng và hàng ngày với ngưỡng 80%/100%

* **Hoàn thành tất cả các điểm xác thực**:
  - Bucket upload S3 tồn tại với việc bật phiên bản, mã hóa, quy tắc vòng đời, và CORS
  - Các bảng DynamoDB (Reviews, Products, Users) tồn tại với streams được bật trên bảng Reviews
  - Ba hàm Lambda đã được kết nối đúng với các trigger và sử dụng các vai trò IAM thích hợp
  - API Gateway và Cognito được tích hợp đúng cách với authorizer hợp lệ và cấu hình CORS
  - Bảng điều khiển và cảnh báo CloudWatch đang hoạt động và cho thấy tình trạng hệ thống khỏe mạnh

Triển khai workshop ReviewSentinal hiện đã hoàn thành và biểu diễn một ứng dụng serverless hoàn chỉnh chức năng chứng minh việc làm việc cùng nhau của các dịch vụ AWS cốt lõi trong một quy trình làm việc thực tế: lưu trữ (S3) → tính toán (Lambda) → cơ sở dữ liệu (DynamoDB Streams) → API (API Gateway) → xác thực (Cognito) → giám sát (CloudWatch) → frontend (ứng dụng React được lưu trữ trên Amplify).