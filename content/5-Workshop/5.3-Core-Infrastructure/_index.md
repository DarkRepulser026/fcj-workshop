---
title: "Core infrastructure"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### Overview

This section creates the shared data and messaging foundation for ReviewSentinal: S3 for raw review uploads, DynamoDB for the review catalog, SNS for alerts, SQS for dead-letter handling, and Secrets Manager for the optional OpenRouter key.

#### Content

1. [S3 buckets](5.03.1-s3-buckets/)
2. [DynamoDB tables](5.03.2-dynamodb-tables/)
3. [Messaging and secrets](5.03.3-messaging-secrets/)

#### Build the foundation

1. Create the raw upload bucket in S3 and keep public access blocked.
2. Create the DynamoDB tables `Reviews`, `Products`, and `Users`.
3. Enable DynamoDB Streams and point-in-time recovery on `Reviews`.
4. Create the SNS topic for negative-review alerts and the SQS dead-letter queue.
5. Store the OpenRouter API key placeholder in Secrets Manager if you want the optional deeper analysis pass later.

#### Notes

+ Use the same region and naming pattern everywhere so the Lambda roles can reference the resources with predictable ARNs.
+ The upload bucket needs CORS configured for browser-based direct uploads.
+ Keep the resource names exactly aligned with the deployment guide, because later sections copy them into IAM policies and environment variables.
