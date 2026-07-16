---
title: "5.3.2 DynamoDB tables"
weight: 2
---

# DynamoDB tables for ReviewSentinal

## Overview

Create the three tables that hold review data, product data, and user data. The `Reviews` table is the main one and needs streams plus a GSI.

### Tables to create

- `Reviews`
- `Products`
- `Users`

### Reviews table

1. Open DynamoDB and choose **Create table**.
2. Table name: `Reviews`.
3. Partition key: `ProductID` as a String.
4. Sort key: `ReviewID` as a String.
5. Choose **Customize**.
6. Set capacity to **On-demand**.
7. Leave encryption as the default DynamoDB-managed key.
8. Create the table.

After creation:

1. Open the `Reviews` table.
2. Enable **DynamoDB Streams** from the **Exports and streams** tab.
3. Choose **New image** as the stream view type.
4. Go to the **Backups** tab and enable **Point-in-time recovery**.
5. Create a GSI named `SentimentIndex`.
6. Use `ProductID` as the partition key and `Sentiment` as the sort key.
7. Project only `ReviewText`, `Rating`, `CreatedAt`, `KeyPhrases`, and `UserID`.

### Products table

1. Create a table named `Products`.
2. Use `ProductID` as the partition key.
3. Leave out the sort key.
4. Use **On-demand** capacity.
5. Enable point-in-time recovery after creation.

### Users table

1. Create a table named `Users`.
2. Use `UserID` as the partition key.
3. Leave out the sort key.
4. Use **On-demand** capacity.
5. Enable point-in-time recovery after creation.

### Notes

- The `Reviews` table stream is needed for the sentiment analyzer Lambda trigger.
- Keep the table names exact because later environment variables and IAM policies reference them directly.
- The GSI is kept minimal on purpose so you only pay for what the code uses.

### Expected result

Three tables should exist, `Reviews` should have streams enabled, and all tables should be on-demand with point-in-time recovery enabled.
