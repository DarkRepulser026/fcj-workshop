---
title: "Worklog Tuần 8"
date: 2026-06-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu Tuần 8:

* Nắm vững các khái niệm cốt lõi của **Amazon CloudFront** và thực hành triển khai CDN với S3 Origin.
* Nghiên cứu và lên kế hoạch kiến trúc cho Capstone Project **ReviewSentinel**.

### Nhiệm vụ cần thực hiện trong tuần này:

| Chủ đề | Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| Amazon CloudFront | **CloudFront Core Concepts & Workshop** <br> - Các khái niệm cốt lõi: CDN, EC2/S3 Origins, Distributions, Custom Error Pages, Origin Groups, Response Headers, Cache Behaviors, Lambda@Edge, giám sát qua Athena/Redshift, best practices <br> - Thực hành **CloudFront với S3 Bucket Origin Workshop**: tạo S3 bucket, tải file index.html, cấu hình CloudFront Distribution, dọn dẹp tài nguyên | 08/06/2026 | 14/06/2026 | AWS Study Group |
| Capstone Project | **Nghiên cứu & Lên kế hoạch ReviewSentinel** (hệ thống phân tích cảm xúc đánh giá sản phẩm bằng AI, AWS Serverless, Event-Driven Architecture) <br> - Lớp Tiếp nhận & Lưu trữ Dữ liệu: S3 presigned URL, webhooks, EventBridge Scheduler, Lambda review-processor, DynamoDB Reviews với GSI và Streams <br> - Lớp Phân tích AI: Amazon Comprehend + Amazon Bedrock Claude 3 Haiku, SNS cảnh báo <br> - Lớp API & Xác thực: WAF → API Gateway → Cognito Authorizer → Lambda api-handler, Lambda upload-handler <br> - Lớp Giao diện Người dùng: React 18 + TypeScript + TailwindCSS trên AWS Amplify, CloudFront CDN, S3 <br> - Lớp Hạ tầng & Giám sát: CloudWatch Logs/Metrics/Alarms, SNS thông báo <br> - Dịch vụ Nền tảng: IAM Least Privilege roles, Terraform (IaC) | 08/06/2026 | 14/06/2026 | AWS Study Group |

# Thành tựu Tuần 8

## Content Delivery Network (CloudFront)
- Nắm rõ các khái niệm cốt lõi: EC2/S3 Origins, Distributions, Custom Error Pages, Origin Groups, Response Headers, Cache Behaviors, Lambda@Edge.
- Thực hành workshop CloudFront với S3 Bucket Origin: tạo bucket, tải file index.html, cấu hình Distribution và dọn dẹp tài nguyên.

## Lên kế hoạch Capstone Project — ReviewSentinel
- Thiết kế lớp Tiếp nhận và Lưu trữ Dữ liệu: S3 presigned URL, webhooks, EventBridge Scheduler, Lambda review-processor, DynamoDB với GSI và Streams.
- Lên kế hoạch lớp Phân tích AI sử dụng **Amazon Comprehend** và **Amazon Bedrock (Claude 3 Haiku)**, kết hợp SNS cảnh báo.
- Thiết kế lớp API & Xác thực: WAF → API Gateway → Cognito Authorizer → Lambda.
- Lên kế hoạch giao diện người dùng bằng React 18 + TypeScript + TailwindCSS trên AWS Amplify, kết hợp CloudFront và S3.
- Thiết kế lớp hạ tầng & giám sát (CloudWatch, SNS) và dịch vụ nền tảng (IAM Least Privilege, Terraform).
