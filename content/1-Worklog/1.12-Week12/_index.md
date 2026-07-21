---
title: "Week 12 Worklog"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:

* Complete end-to-end implementation of the ReviewSentinal workshop project
* Implement all infrastructure, backend services, and frontend integration
* Validate the complete pipeline with sample test data
* Prepare for cleanup and documentation

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Implement Lambda functions: review_processor, sentiment_analyzer, api_handler<br>- Configure IAM roles with least-privilege policies<br>- Deploy Lambda functions with correct handlers and environment variables | 08/07/2026 | 10/07/2026      | AWS Study Group                           |
| 3   | - Configure API Gateway with Cognito authorizer<br>- Enable CORS on all public resources<br>- Deploy REST API to dev stage<br>- Grant Lambda invoke permissions from API Gateway                             | 11/07/2026 | 12/07/2026      | AWS Study Group                           |
| 4   | - Set up S3 bucket notifications to trigger review_processor Lambda<br>- Configure DynamoDB Streams trigger for sentiment_analyzer Lambda<br>- Add filter criteria for INSERT events with PENDING status      | 13/07/2026 | 14/07/2026      | AWS Study Group                           |
| 5   | - Build and configure Vite React TypeScript frontend<br>- Set environment variables (API URL, Cognito settings)<br>- Deploy frontend to Amplify<br>- Update Cognito callback/sign-out URLs and S3 CORS      | 15/07/2026 | 16/07/2026      | AWS Study Group                           |
| 6   | - Run end-to-end validation: Cognito sign-up, file upload, pipeline processing<br>- Verify CloudWatch dashboard shows healthy metrics<br>- Test optional OpenRouter path if API key available        | 17/07/2026 | 18/07/2026      | AWS Study Group                           |

### Week 12 Achievements:

* **Successfully implemented all three Lambda functions** with appropriate IAM roles:
  - `review_processor`: Validates S3 uploads, writes initial review records to DynamoDB
  - `sentiment_analyzer`: Processes DynamoDB Streams, uses Comprehend for sentiment analysis, optionally calls OpenRouter, sends completion emails via Amazon SES
  - `api_handler`: Serves REST API endpoints for products, reviews, uploads, and analysis requests

* **Configured complete event-driven architecture**:
  - S3 object-created events trigger review_processor Lambda (with uploads/ prefix filter)
  - DynamoDB Streams on Reviews table trigger sentiment_analyzer Lambda (filtered for INSERT events where ProcessingStatus=PENDING)
  - Proper error handling configured with DLQ (lambda-dlq) for all Lambda functions

* **Deployed fully functional API Gateway**:
  - REST API with Cognito authorizer protecting all endpoints
  - CORS configured on all public resources (allowing Content-Type, Authorization, X-Api-Key, X-Amz-Security-Token)
  - dev stage deployed with accessible Invoke URL
  - Lambda invoke permissions properly granted from API Gateway

* **Implemented complete frontend integration**:
  - Built Vite React TypeScript application with Tailwind CSS styling
  - Configured environment variables pointing to deployed API Gateway and Cognito resources
  - Successfully deployed to AWS Amplify with custom domain
  - Updated Cognito User Pool callback/sign-out URLs and S3 bucket CORS allowed origins to include frontend domain

* **Validated end-to-end pipeline functionality**:
  - Successfully signed up and signed in via Cognito Hosted UI
  - Uploaded sample review files through browser interface
  - Verified processor Lambda wrote initial records to DynamoDB Reviews table
  - Verified analyzer Lambda processed streams, updated records with sentiment analysis, and sent completion emails via SES
  - Confirmed CloudWatch dashboard showed healthy invocation and error metrics
  - Tested optional OpenRouter path by storing API key in Secrets Manager and enabling deep analysis

* **Implemented comprehensive observability**:
  - Created CloudWatch dashboard showing Lambda invocations, errors, and duration metrics
  - Configured Lambda error alarms (5+ errors in 5-minute window) sending notifications via SES
  - Configured API latency alarm (>5000ms duration) sending notifications via SES
  - Set up monthly and daily budget alerts with 80%/100% thresholds

* **Completed all validation checkpoints**:
  - S3 upload bucket exists with versioning, encryption, lifecycle rules, and CORS enabled
  - DynamoDB tables (Reviews, Products, Users) present with streams enabled on Reviews table
  - All three Lambda functions wired to correct triggers and using appropriate IAM roles
  - API Gateway and Cognito properly integrated with valid authorizer and CORS configuration
  - CloudWatch dashboard and alarms active and showing healthy system status

The ReviewSentinal workshop implementation is now complete and represents a fully functional serverless application demonstrating core AWS services working together in a realistic workflow: storage (S3) → compute (Lambda) → database (DynamoDB Streams) → API (API Gateway) → authentication (Cognito) → monitoring (CloudWatch) → frontend (Amplify hosted React app).