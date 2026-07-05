---
title: "Worklog Tuần 10"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu Tuần 10:

* Triển khai ứng dụng serverless bằng **AWS SAM** (Infrastructure as Code).
* Xây dựng luồng xác thực với **Amazon Cognito**.
* Thiết lập SSL cho ứng dụng với ACM, Route 53 và CloudFront.
* Xây dựng hệ thống xử lý đơn hàng bất đồng bộ với **SQS** và **SNS**.

### Nhiệm vụ cần thực hiện trong tuần này:

| Chủ đề | Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| AWS SAM | **Serverless: Triển khai ứng dụng với AWS SAM Workshop** <br> - Framework IaC dạng YAML <br> - Xây dựng lại ứng dụng web bằng SAM <br> - Kiểm thử và dọn dẹp tài nguyên | 22/06/2026 | 28/06/2026 | AWS Study Group |
| Amazon Cognito | **Serverless: Xác thực với Amazon Cognito Workshop** <br> - User Pools, Identity Pools <br> - Luồng xác thực kết hợp <br> - Triển khai Lambda/API <br> - Kiểm thử end-to-end | 22/06/2026 | 28/06/2026 | AWS Study Group |
| SSL Setup | **Serverless: Thiết lập SSL Workshop** <br> - AWS Certificate Manager, Amazon Route 53 <br> - CloudFront với S3 origin <br> - Tạo domain/Hosted Zone, yêu cầu chứng chỉ SSL <br> - Dọn dẹp tài nguyên | 22/06/2026 | 28/06/2026 | AWS Study Group |
| SQS & SNS | **Serverless: Xử lý Đơn hàng với SQS và SNS Workshop** <br> - Amazon SQS, Amazon SNS <br> - Luồng xử lý đơn hàng (checkout → SQS/SNS → admin xử lý qua API) <br> - Triển khai Lambda/API <br> - Kiểm thử, dọn dẹp tài nguyên | 22/06/2026 | 28/06/2026 | AWS Study Group |

# Thành tựu Tuần 10

## Infrastructure as Code (AWS SAM)
- Xây dựng lại ứng dụng web bằng framework **AWS SAM** (YAML), thực hiện kiểm thử và dọn dẹp tài nguyên.

## Xác thực với Amazon Cognito
- Triển khai **User Pools** và **Identity Pools**, xây dựng luồng xác thực kết hợp.
- Triển khai Lambda/API tích hợp Cognito và thực hiện kiểm thử end-to-end.

## Thiết lập SSL
- Cấu hình **AWS Certificate Manager**, **Amazon Route 53** và **CloudFront** với S3 origin.
- Tạo domain/Hosted Zone, yêu cầu chứng chỉ SSL và dọn dẹp tài nguyên sau khi hoàn tất.

## Xử lý Đơn hàng Bất đồng bộ (SQS & SNS)
- Xây dựng luồng xử lý đơn hàng: checkout → SQS/SNS → admin xử lý qua API.
- Triển khai Lambda/API cho luồng xử lý, kiểm thử và dọn dẹp tài nguyên.
