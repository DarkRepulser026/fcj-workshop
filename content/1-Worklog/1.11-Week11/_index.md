---
title: "Week 11 Worklog"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives
* Finalize the overall system architecture for ReviewSentinel (edge, app, processing, analytics, monitoring layers).
* Define the security model: Cognito auth flow, IAM least-privilege roles, API Gateway authorization.
* Design the DynamoDB data model (Reviews, Products, Users tables and access patterns).
* Draft the Lambda function specifications (review-processor, sentiment-analyzer, API handler) and their triggers.
* Prepare infrastructure-as-code approach and development environment.
* Prepare foundational infrastructure components for implementation.

---

### Tasks to be carried out this week

| Day | Task | Start Date | Completion Date | Reference Material |
|-----|------|-------------|------------------|--------------------|
| 2 | Review and finalize ReviewSentinel architecture diagram (edge/app/processing/analytics layers). <br>- Confirm AWS service choices and data flow. | 29/06/2026 | 29/06/2026 | AWS Study Group |
| 3 | Design security model: Cognito user pool, JWT-based API Gateway authorizer, IAM role scoping. <br>- Document threat considerations for a demo-scale project. | 30/06/2026 | 30/06/2026 | AWS Study Group |
| 4 | Design DynamoDB schema (Reviews, Products, Users) with keys, GSIs, and access patterns. <br>- Plan S3 bucket layout and event triggers. | 01/07/2026 | 01/07/2026 | AWS Study Group |
| 5 | Draft Lambda function specs: `review_processor`, `sentiment_analyzer`, `api_handler`. <br>- Define input/output contracts and error-handling approach. | 02/07/2026 | 02/07/2026 | AWS Study Group |
| 6   | - Finalize infrastructure-as-code approach and development environment<br>- Prepare foundational components (S3 buckets, DynamoDB tables) for implementation | 03/07/2026 | 03/07/2026 | AWS Study Group |

---

### Week 11 Achievements

#### **1. Finalized System Architecture**
I reviewed and locked down the ReviewSentinel architecture (v5), covering the edge/security layer, application layer (API Gateway, Cognito, API Lambda), processing layer (S3-triggered and stream-triggered Lambdas), and analytics layer (Comprehend, Bedrock). Since this is a study/demo project, I deliberately kept the design simple and avoided over-provisioning for scale, prioritizing clarity and correctness over production-grade throughput.

#### **2. Designed the Security Model**
I planned the authentication and authorization flow: Cognito User Pool for signup/login, JWT tokens validated by an API Gateway Lambda authorizer, and IAM roles scoped to least privilege per Lambda function. I also noted baseline security practices to apply later — no public S3 buckets, encryption at rest for DynamoDB, and no sensitive data written to logs.

#### **3. Designed the Data Model**
I defined the DynamoDB table structure for Reviews, Products, and Users, including primary keys and the GSIs needed to support the planned query patterns (e.g., reviews by product, analytics by date range). I also mapped out the S3 bucket layout for raw review uploads and the event notifications that will trigger downstream processing.

#### **4. Drafted Lambda Function Specifications**
I wrote specifications for the three core Lambda functions — `review_processor` (S3 trigger, validation/cleaning/dedup), `sentiment_analyzer` (DynamoDB Streams trigger, Comprehend + optional Bedrock insights), and `api_handler` (API Gateway REST endpoints). Each spec includes expected inputs/outputs and a consistent error-handling/response format to reduce integration issues during implementation.

#### **5. Prepared Infrastructure Approach and Foundation**
I defined the infrastructure-as-code approach and prepared the development environment. I finalized the specifications for foundational components (S3 buckets and DynamoDB tables) so that Week 12 can focus on implementing the application logic without revisiting infrastructure planning.

#### **6. Set Groundwork for Week 12**
With architecture, security model, data model, and Lambda specs finalized, and foundational infrastructure components prepared, the project is positioned to move into full implementation next week: deploying Lambda functions, connecting API Gateway with Cognito authorization, building the React frontend integration, and validating the end-to-end flow with CloudWatch monitoring.

---