# AWS AI Receipt Automation

A serverless AWS project that automatically processes receipt images, extracts useful information using AI, stores the results, and sends email notifications.

This project was built as a hands-on AWS Cloud project to practice serverless architecture, event-driven systems, IAM, storage, AI services, databases, and email services.

---

## Architecture

```text
                    ┌──────────────┐
                    │     User     │
                    └──────┬───────┘
                           │
                           │ Upload Receipt
                           ▼
                    ┌──────────────┐
                    │   Amazon S3  │
                    │ Receipt File │
                    └──────┬───────┘
                           │
                    S3 Event Trigger
                           │
                           ▼
                    ┌──────────────┐
                    │    AWS       │
                    │    Lambda    │
                    └──────┬───────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ Amazon Textract  │
                  │ OCR / Extraction │
                  └────────┬─────────┘
                           │
                           ▼
                    ┌──────────────┐
                    │   DynamoDB   │
                    │ Store Results │
                    └──────────────┘
                           │
                           ▼
                    ┌──────────────┐
                    │  Amazon SES  │
                    │ Email Result │
                    └──────────────┘
