---
title: "5.4.3 Event triggers"
weight: 3
---

# Event triggers for ReviewSentinal

## Overview

Wire the storage and database events into the Lambda functions so the pipeline runs automatically. This step connects the infrastructure created earlier to the business logic created in the previous subpage.

### Triggers to configure

- S3 object-created event for the processor Lambda
- DynamoDB Streams trigger for the analyzer Lambda
- Optional daily EventBridge schedule for the API Lambda

## Step-by-step

### 1. Wire the S3 trigger

1. Open the `review-sentiment-analyzer-processor` Lambda.
2. Choose **Add trigger**.
3. Select **S3**.
4. Choose the raw upload bucket.
5. Set the event type to **All object create events**.
6. Add the prefix `uploads/`.
7. Confirm the recursive invocation warning and add the trigger.

### 2. Wire the DynamoDB stream trigger

1. Open the `review-sentiment-analyzer-analyzer` Lambda.
2. Choose **Add trigger**.
3. Select **DynamoDB**.
4. Choose the `Reviews` table.
5. Keep the batch size at `100` and the starting position at **Latest**.
6. Add the filter criteria so the Lambda only fires on `INSERT` events where `ProcessingStatus` is `PENDING`.
7. Enable split batch on error.
8. Add the trigger.

### 3. Add the optional EventBridge schedule

1. Open the `review-sentiment-analyzer-api` Lambda.
2. Choose **Add trigger**.
3. Select **EventBridge (CloudWatch Events)**.
4. Create a new rule named `review-sentiment-analyzer-daily-digest`.
5. Use the schedule expression `rate(1 day)`.
6. Add the trigger.

### Notes

1. The S3 trigger starts the ingestion path.
2. The DynamoDB stream trigger must filter out updates from the analyzer itself.
3. The EventBridge rule is optional, but it is part of the full deployment flow.

### Expected result

The ingestion path should start from S3, continue through DynamoDB Streams, and optionally feed the daily digest flow through EventBridge.
