
---

# 4. `docs/security.md`

This is important because it makes the project look much more like a real cloud engineering project.

Use:

```markdown
# Security

## Security Overview

The application uses AWS Identity and Access Management (IAM) and AWS managed security controls to protect access to cloud resources.

The main security principles are:

- Least privilege
- No hard-coded credentials
- Controlled access to S3
- Controlled access to DynamoDB
- Controlled access to Textract
- Controlled access to SES
- CloudWatch logging

---

## IAM

The Lambda function runs using an IAM execution role.

The role should grant only the permissions required by the application.

Required access includes:

```text
S3
 └── Read receipt objects

Textract
 └── Analyze receipts

DynamoDB
 └── Write receipt records

SES
 └── Send notification emails

CloudWatch
 └── Write Lambda logs
