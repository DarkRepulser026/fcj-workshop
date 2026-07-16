---
title: "5.03.3 Messaging and secrets"
weight: 3
---

# Messaging and secrets for ReviewSentinal

## Overview

Create the dead-letter queue, SNS alert topic, and optional secret that the Lambdas will use later.

### SQS dead-letter queue

1. Open SQS and choose **Create queue**.
2. Select **Standard**.
3. Name the queue `lambda-dlq`.
4. Confirm **SSE-SQS** encryption is on.
5. Set message retention to 14 days.
6. Create the queue.
7. Copy the queue ARN from the details page.

### SNS alert topic

1. Open SNS and go to **Topics** → **Create topic**.
2. Select **Standard**.
3. Name the topic `sentiment-alerts`.
4. Keep encryption on with the AWS managed SNS key.
5. Create the topic.
6. Create an email subscription using your own email address.
7. Confirm the subscription from your inbox.
8. Copy the topic ARN.

### Secrets Manager secret

1. Open Secrets Manager and choose **Store a new secret**.
2. Pick **Other type of secret**.
3. Use the **Plaintext** tab, not key/value pairs.
4. Enter a placeholder value such as `REPLACE_ME_LATER`.
5. Leave encryption on the default AWS-managed key.
6. Name the secret `review-sentiment-analyzer-openrouter-api-key`.
7. Skip rotation and store it.
8. Copy the secret ARN.

### Notes

- Keep the placeholder secret empty of structure because the Lambda reads the raw string directly.
- The DLQ is used by the Lambdas for async failure handling.
- You will paste the ARN values into IAM policies in the next section.

### Expected result

You should have an SQS DLQ ARN, an SNS topic ARN with a confirmed email subscription, and a Secrets Manager secret ARN ready for the IAM roles.
