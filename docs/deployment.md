# System Architecture

## Architecture Overview

The application follows a serverless, event-driven architecture built using AWS managed services.

The main processing pipeline is:

```text
Receipt Upload
      │
      ▼
Amazon S3
      │
      │ Object Created Event
      ▼
ReceiptProcessor Lambda
      │
      ├──────────────► Amazon Textract
      │                  │
      │                  └── Extract receipt data
      │
      ├──────────────► Amazon DynamoDB
      │                  │
      │                  └── Store receipt data
      │
      └──────────────► Amazon SES
                         │
                         └── Send email notification
