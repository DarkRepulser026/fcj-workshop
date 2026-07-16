---
title: "5.4.1 IAM roles"
weight: 1
---

# IAM roles for the processing layer

## Overview

Create one least-privilege IAM role for each Lambda function used by ReviewSentinal. Do not reuse a shared role: the processor, analyzer, and API handler each touch a different set of resources.

### Roles to create

- `review-processor-role`
- `sentiment-analyzer-role`
- `api-handler-role`

### Common requirements

- Trust policy: `lambda.amazonaws.com`
- CloudWatch Logs permissions for all three roles
- SQS send permissions for the DLQ
- Scoped S3, DynamoDB, SNS, and Secrets Manager access based on the Lambda function

## Step-by-step

### 1. Create the processor role

1. Open the IAM console and go to **Roles**.
2. Choose **Create role**.
3. Select **AWS service** as the trusted entity.
4. Choose **Lambda** as the use case.
5. Continue without attaching any AWS managed policy.
6. Name the role `review-processor-role` and create it.
7. Open the role and create an inline policy in the **JSON** editor.
8. Paste the processor policy from the deployment guide and replace `<ACCOUNT_ID>` with your real account ID.
9. Save the policy as `review-processor-policy`.

### 2. Create the sentiment analyzer role

1. Repeat the same create-role flow.
2. Name the role `sentiment-analyzer-role`.
3. Create a second inline policy named `sentiment-analyzer-policy`.
4. Paste the analyzer policy from the deployment guide.
5. Replace `<ACCOUNT_ID>` and the Secrets Manager ARN with your real values.
6. Confirm the separate `DynamoDBStreamsAccess` statement is present.

### 3. Create the API handler role

1. Create a third IAM role for Lambda.
2. Name it `api-handler-role`.
3. Attach the `api-handler-policy` inline policy.
4. Paste the full policy from the deployment guide.
5. Replace `<ACCOUNT_ID>` and the secret ARN with your real values.

### Notes

1. The processor role needs S3 read access and DynamoDB write access.
2. The analyzer role needs stream access in addition to table access.
3. The API handler role needs the broadest table permissions because it serves the REST API and scheduled digest path.
4. Keep CloudWatch Logs permissions in every role so each function can write logs on first invocation.

### Expected result

You should end this step with three IAM roles that are ready to attach to the Lambda functions in the next subpage.
