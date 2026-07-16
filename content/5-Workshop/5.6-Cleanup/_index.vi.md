---
title: "Dọn dẹp"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

Chúc mừng bạn đã hoàn thành hướng dẫn triển khai.

#### Nội dung

1. [Dọn dẹp frontend](5.06.1-frontend/)
2. [Dọn dẹp backend và dữ liệu](5.06.2-backend-data/)
3. [Xác minh](5.06.3-verification/)

#### Dọn dẹp

1. Xóa frontend được deploy bằng Amplify hoặc static hosting nếu bạn đã tạo trong workshop.
2. Xóa stage API Gateway và REST API nếu không còn cần endpoint.
3. Xóa các Lambda function và IAM role của chúng.
4. Làm rỗng rồi xóa bucket S3 dùng để upload.
5. Xóa các bảng DynamoDB, SNS topic, SQS queue và Secrets Manager secret.
6. Xác nhận CloudWatch dashboard và alarm đã được gỡ bỏ nếu bạn không muốn chúng tiếp tục tạo chi phí hoặc cảnh báo.

#### Kết quả cuối

Sau khi dọn dẹp, tài khoản không nên còn bất kỳ tài nguyên ReviewSentinal nào.
