# Architecture Description

## Overview

Automating My Life with AWS & AI is a serverless cloud application that automatically processes uploaded receipts.

The system uses Amazon S3 as the input storage layer. When a receipt is uploaded to the S3 bucket, an S3 event triggers the `ReceiptProcessor` AWS Lambda function.

The Lambda function processes the receipt using Amazon Textract, stores the extracted information in Amazon DynamoDB, and sends a notification email using Amazon SES.

## AWS Services

| Service | Purpose |
|---|---|
| Amazon S3 | Stores uploaded receipt images/documents |
| AWS Lambda | Executes the receipt processing logic |
| Amazon Textract | Extracts structured information from receipts |
| Amazon DynamoDB | Stores processed receipt data |
| Amazon SES | Sends receipt processing notifications |

## Data Flow

1. A receipt is uploaded to the Amazon S3 bucket.
2. Amazon S3 generates an object-created event.
3. The event triggers the `ReceiptProcessor` Lambda function.
4. Lambda retrieves and verifies the receipt from S3.
5. Lambda sends the receipt to Amazon Textract using `AnalyzeExpense`.
6. Textract extracts information such as:
   - Vendor
   - Date
   - Total amount
   - Items
   - Prices
   - Quantities
7. Lambda stores the extracted data in the `Receipts` DynamoDB table.
8. Lambda sends a notification email using Amazon SES.
9. The processed receipt information is available in DynamoDB.

## AWS Region

The project is deployed in:

`eu-west-3` — Europe (Paris)
