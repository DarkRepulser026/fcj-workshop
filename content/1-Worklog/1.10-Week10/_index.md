---
title: "Week 10 Worklog"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Week 10 Objectives:

* Deploy a serverless application using **AWS SAM** (Infrastructure as Code).
* Build an authentication flow with **Amazon Cognito**.
* Set up SSL for the application using ACM, Route 53, and CloudFront.
* Build an asynchronous order-processing system using **SQS** and **SNS**.

### Tasks to be carried out this week:

| Topic | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| AWS SAM | **Serverless: Deploying an Application with AWS SAM Workshop** <br> - YAML-based IaC framework <br> - Rebuilt the web app using SAM <br> - Testing and resource cleanup | 06/22/2026 | 06/28/2026 | AWS Study Group |
| Amazon Cognito | **Serverless: Authentication with Amazon Cognito Workshop** <br> - User Pools, Identity Pools <br> - Combined authentication flow <br> - Lambda/API deployment <br> - End-to-end testing | 06/22/2026 | 06/28/2026 | AWS Study Group |
| SSL Setup | **Serverless: SSL Setup Workshop** <br> - AWS Certificate Manager, Amazon Route 53 <br> - CloudFront with an S3 origin <br> - Created a domain/Hosted Zone, requested an SSL certificate <br> - Resource cleanup | 06/22/2026 | 06/28/2026 | AWS Study Group |
| SQS & SNS | **Serverless: Order Processing with SQS and SNS Workshop** <br> - Amazon SQS, Amazon SNS <br> - Order-processing flow (checkout → SQS/SNS → admin processes via API) <br> - Lambda/API deployment <br> - Testing and resource cleanup | 06/22/2026 | 06/28/2026 | AWS Study Group |

# Week 10 Achievements

## Infrastructure as Code (AWS SAM)
- Rebuilt the web app using the **AWS SAM** framework (YAML), performed testing, and cleaned up resources.

## Authentication with Amazon Cognito
- Deployed **User Pools** and **Identity Pools**, and built a combined authentication flow.
- Deployed Lambda/API integrated with Cognito and performed end-to-end testing.

## SSL Setup
- Configured **AWS Certificate Manager**, **Amazon Route 53**, and **CloudFront** with an S3 origin.
- Created a domain/Hosted Zone, requested an SSL certificate, and cleaned up resources afterward.

## Asynchronous Order Processing (SQS & SNS)
- Built an order-processing flow: checkout → SQS/SNS → admin processes via API.
- Deployed Lambda/API for the processing flow, tested it, and cleaned up resources.
