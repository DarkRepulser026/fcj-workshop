---
title: "Proposal"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# ReviewSentinel: AI-Powered Product Review Sentiment Analyzer
## A Serverless AWS Solution for Automated Review Analysis

### 1. Executive Summary

ReviewSentinel is a study/demo project that builds a small, fully serverless pipeline on AWS to automatically collect product reviews, analyze their sentiment with AI, and surface the results on a live dashboard. It is sized for a few hundred to a few thousand reviews rather than production traffic, using Amazon Comprehend and Amazon Bedrock (Claude 3 Haiku) for sentiment analysis, DynamoDB and S3 for storage, and a React dashboard for visualization. The goal is to demonstrate a complete, working, secure pipeline end-to-end — not to build a commercial product — while keeping monthly cost close to $0 by relying on AWS Free Tier and tearing down resources between sessions.

### 2. Problem Statement

**What's the Problem?**
Reading through product reviews one by one to gauge how customers feel does not scale even at small volume, and doing it manually gives no consistent, repeatable way to flag negative feedback quickly. There is no lightweight, low-cost way to automatically score sentiment and see trends without either building a heavy custom system or paying for a full commercial analytics platform.

**The Solution**
ReviewSentinel ingests review files (CSV/JSON) through S3, automatically validates and cleans them with Lambda, stores them in DynamoDB, and runs each review through Amazon Comprehend for sentiment scoring (with an optional Amazon Bedrock pass for deeper insight). Strongly negative reviews trigger an email alert via SNS. A React dashboard, protected by Amazon Cognito login, shows sentiment breakdowns and trends per product. Everything is provisioned with Terraform so the whole environment can be deployed and destroyed on demand.

**Benefits**
The project gives hands-on experience with a realistic serverless + AI architecture pattern (event-driven ingestion → AI enrichment → authenticated API → dashboard) that generalizes to many other use cases. It produces a working reference implementation and a reusable Terraform base for future projects. Because it runs on Free Tier at demo scale, there is effectively no ongoing cost as long as resources are torn down between uses.

### 3. Solution Architecture

The platform uses a serverless, event-driven AWS architecture. A review file uploaded to S3 triggers a Lambda function that validates and cleans the data before storing it in DynamoDB. Writing to DynamoDB triggers a second Lambda (via DynamoDB Streams) that calls Amazon Comprehend to score sentiment, optionally enriching results with Amazon Bedrock. Negative results publish an alert through SNS. A Cognito-authenticated API Gateway + Lambda layer serves the React dashboard, which visualizes the data.

```
Upload (CSV/JSON)
      │
      ▼
Amazon S3 (raw-reviews bucket)
      │  S3 event
      ▼
AWS Lambda — review-processor
  (validate, clean, de-duplicate)
      │
      ▼
Amazon DynamoDB (Reviews / Products / Users)
      │  DynamoDB Stream
      ▼
AWS Lambda — sentiment-analyzer
  (Amazon Comprehend + optional Bedrock)
      │
      ▼
Amazon SNS ── email alert on negative sentiment

Amazon Cognito ── API Gateway (authorizer) ── AWS Lambda — api-handler
      │
      ▼
React Dashboard (S3 + CloudFront / Amplify)

Amazon CloudWatch ── logs, dashboards, alarms across all Lambda functions
```

**AWS Services Used**
- **Amazon S3**: Stores raw uploaded review files and processed reports (2 buckets), public access blocked, encrypted at rest.
- **AWS Lambda**: Three functions — review-processor (validation/cleaning), sentiment-analyzer (Comprehend/Bedrock), api-handler (REST API).
- **Amazon DynamoDB**: Three tables (Reviews, Products, Users) with GSIs for query patterns and Streams enabled for the sentiment pipeline.
- **Amazon Comprehend**: Baseline sentiment, key phrase, and entity extraction.
- **Amazon Bedrock (Claude 3 Haiku)**: Optional deeper-insight pass, used selectively to control cost.
- **Amazon API Gateway**: REST API with a Cognito authorizer and request validation.
- **Amazon Cognito**: User authentication (JWT) for the dashboard and API.
- **Amazon SNS**: Email alerts on strongly negative reviews.
- **Amazon SQS**: Dead-letter queue for failed processing events.
- **Amazon CloudWatch**: Logs, dashboards, and alarms (Lambda errors, API latency).
- **Terraform**: Infrastructure as Code for the entire stack, enabling clean deploy/teardown.

**Component Design**
- **Ingestion**: Users upload CSV/JSON review files via presigned S3 URLs issued by the API.
- **Processing**: review-processor Lambda validates schema, de-duplicates, and cleans text before writing to DynamoDB; failures land in an SQS dead-letter queue instead of being dropped.
- **AI Analysis**: sentiment-analyzer Lambda runs on new DynamoDB records, calling Comprehend (and optionally Bedrock) to score sentiment and extract key phrases/entities.
- **Alerting**: SNS publishes an email notification when sentiment is strongly negative.
- **API & Auth**: Cognito issues JWTs; API Gateway verifies every request before it reaches api-handler, which serves products, reviews, and analytics endpoints.
- **Dashboard**: A React + TypeScript app shows product lists, an upload interface, and sentiment charts (pie/line/bar via Recharts).

### 4. Technical Implementation

**Implementation Phases**
The project follows four phases:
- **Foundation & IaC Setup**: Set up the AWS sandbox account, initialize Terraform, and define S3 buckets, DynamoDB tables, and base IAM roles (Days 1–3).
- **Backend Processing & AI Pipeline**: Build and deploy the review-processor and sentiment-analyzer Lambda functions, wire up S3 events and DynamoDB Streams, integrate Comprehend/Bedrock, and configure the SNS alert (Days 4–11).
- **API, Auth & Frontend**: Set up Cognito, deploy the authenticated API Gateway + api-handler Lambda, and build/deploy the React dashboard (Days 12–18).
- **Testing & Hardening**: Run integration tests against sample data, verify IAM least-privilege and encryption settings, and finalize documentation (Days 19–21).

**Technical Requirements**
- **Backend**: Python 3.9+ for Lambda functions, boto3 for AWS SDK calls, Terraform for infrastructure.
- **AI Services**: Amazon Comprehend (sentiment, key phrases, entities) and Amazon Bedrock model access (Claude 3 Haiku) enabled in the target region.
- **Frontend**: Node.js 18+, React + TypeScript, Recharts for charts, deployed via Amplify or S3 + CloudFront.
- **Security**: Cognito user pool for authentication, least-privilege IAM role per Lambda function, encryption at rest (S3/DynamoDB) and in transit (TLS/HTTPS), no public S3 access, no hard-coded credentials.
- **Region**: Single region (ap-southeast-1), serverless-only — no EC2 or self-managed databases.

### 5. Timeline & Milestones

**Project Timeline** (~3 weeks, part-time, single contributor — compresses with more people working in parallel)
- **Week 1**: Foundation & IaC setup; backend processing pipeline (upload → validate → store) working end-to-end.
- **Week 2**: AI sentiment pipeline live (Comprehend + optional Bedrock); SNS alerts verified; authenticated API deployed.
- **Week 3**: React dashboard built and deployed; full integration testing; security self-review; documentation and teardown instructions finalized.

### 6. Budget Estimation

Because this is a study/demo project rather than a production deployment, the estimate below reflects both a demo-scale reality check and a reference point at higher (50,000 reviews/month) volume to show the architecture scales without redesign.

**At demo scale (a few hundred reviews, tested over a few days)**
- Nearly every service below falls within AWS Free Tier.
- Comprehend and Bedrock usage costs at most a few dollars for testing volumes.
- Running `terraform destroy` between work sessions avoids ongoing DynamoDB/CloudWatch charges.
- **Estimated cost: under $5 for the full study/demo period.**

**Reference: at 50,000 reviews/month (for scale illustration only)**

| Service | Monthly Cost (USD) | Notes |
|---|---|---|
| AWS Lambda | $0.05 | ~100K invocations/month, mostly Free Tier |
| Amazon DynamoDB | $75.00 | Pay-per-request: ~50K writes, ~200K reads |
| Amazon S3 | $0.05 | Storage + API calls |
| Amazon API Gateway | $3.50 | ~10K requests/month |
| Amazon Comprehend | $25.00 | 50K texts, ~100 units/review |
| Amazon Bedrock (optional) | $15.00 | ~50K texts, sampled use recommended |
| Amazon Cognito | Free | Under 50K monthly active users |
| Amazon CloudWatch | $5.00 | Logs, dashboards, alarms |
| Amazon SNS | $0.50 | Alert notifications |
| **Total** | **≈ $124/month** | ≈ $0.0025 per review at 50K/month |

### 7. Risk Assessment

**Risk Matrix**
- Bedrock cost/throttling if called on every review: Medium impact, medium probability.
- Misconfigured IAM permissions on a Lambda role: High impact, low probability.
- Idle resources left running after the demo (API Gateway cache, CloudWatch logs): Low impact, medium probability.
- Sample/synthetic test data not representative enough to validate sentiment accuracy: Low impact, low probability.

**Mitigation Strategies**
- Use Comprehend as the default sentiment path; call Bedrock only on a sample or on demand.
- Review each Lambda's IAM role against the specific actions/resources it actually needs; avoid wildcard permissions.
- Document and run `terraform destroy` after each work session; set a budget alarm as a backstop.
- Use a varied, manually labeled test set spanning positive, negative, and neutral reviews.

**Contingency Plans**
- If Bedrock is unavailable or over budget, fall back to Comprehend-only scoring — the pipeline still functions.
- If a Terraform apply fails partway, `terraform destroy` and redeploy from a clean state rather than patching manually.

### 8. Expected Outcomes

**Technical Improvements**
A working, end-to-end demonstration of an event-driven, AI-enriched data pipeline: upload → validate → store → analyze → alert → visualize, with authenticated APIs and encrypted data throughout.

**Learning Outcomes**
Hands-on experience with Infrastructure as Code (Terraform), serverless event-driven design (S3 events, DynamoDB Streams), AI service integration (Comprehend, Bedrock), and applying security fundamentals (least-privilege IAM, encryption, authenticated APIs) without over-building for a scale the project doesn't need.

**Reusability**
The Terraform stack and Lambda code serve as a reusable starting point for future serverless + AI projects, and the sample data and test scripts make the pipeline easy to re-demo or extend later.