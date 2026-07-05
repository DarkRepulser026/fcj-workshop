---
title: "Week 8 Worklog"
date: 2026-06-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Week 8 Objectives:

* Master the core concepts of **Amazon CloudFront** and practice deploying a CDN with an S3 origin.
* Research and plan the architecture for the **ReviewSentinel** Capstone Project.

### Tasks to be carried out this week:

| Topic | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Amazon CloudFront | **CloudFront Core Concepts & Workshop** <br> - Core concepts: CDN, EC2/S3 Origins, Distributions, Custom Error Pages, Origin Groups, Response Headers, Cache Behaviors, Lambda@Edge, monitoring via Athena/Redshift, best practices <br> - Completed the **CloudFront with S3 Bucket Origin Workshop**: created an S3 bucket, uploaded an index.html file, configured a CloudFront Distribution, and cleaned up resources | 06/08/2026 | 06/14/2026 | AWS Study Group |
| Capstone Project | **Research & Planning for ReviewSentinel** (an AI-powered product-review sentiment analysis system built on AWS Serverless, Event-Driven Architecture) <br> - Ingestion & Storage Layer: S3 presigned URLs, webhooks, EventBridge Scheduler, Lambda review-processor, DynamoDB Reviews with GSI and Streams <br> - AI Analysis Layer: Amazon Comprehend + Amazon Bedrock Claude 3 Haiku, SNS alerts <br> - API & Auth Layer: WAF → API Gateway → Cognito Authorizer → Lambda api-handler, Lambda upload-handler <br> - UI Layer: React 18 + TypeScript + TailwindCSS on AWS Amplify, CloudFront CDN, S3 <br> - Infrastructure & Monitoring Layer: CloudWatch Logs/Metrics/Alarms, SNS notifications <br> - Platform Services: IAM Least Privilege roles, Terraform (IaC) | 06/08/2026 | 06/14/2026 | AWS Study Group |

# Week 8 Achievements

## Content Delivery Network (CloudFront)
- Gained a clear understanding of core concepts: EC2/S3 Origins, Distributions, Custom Error Pages, Origin Groups, Response Headers, Cache Behaviors, Lambda@Edge.
- Completed the CloudFront with S3 Bucket Origin workshop: created a bucket, uploaded an index.html file, configured a Distribution, and cleaned up resources.

## Planning the Capstone Project — ReviewSentinel
- Designed the Ingestion and Storage Layer: S3 presigned URLs, webhooks, EventBridge Scheduler, Lambda review-processor, DynamoDB with GSI and Streams.
- Planned the AI Analysis Layer using **Amazon Comprehend** and **Amazon Bedrock (Claude 3 Haiku)**, combined with SNS alerts.
- Designed the API & Auth Layer: WAF → API Gateway → Cognito Authorizer → Lambda.
- Planned the UI Layer using React 18 + TypeScript + TailwindCSS on AWS Amplify, combined with CloudFront and S3.
- Designed the Infrastructure & Monitoring Layer (CloudWatch, SNS) and Platform Services (IAM Least Privilege, Terraform).
