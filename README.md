import { Callout } from '@components/Callout'
import { CodeBlock } from '@components/CodeBlock'

# 🚀 AWS Lambda Functions

This repository contains a collection of **AWS Lambda functions** written in **Python**, designed to perform a variety of serverless tasks. These functions interact with AWS services such as **DynamoDB**, **API Gateway**, and more.

---

## 📁 Repository Structure

```text
aws-lambda-functions/
│
├── function_name_1/
│   ├── function.py
│   ├── requirements.txt
│   └── README.md
│
├── function_name_2/
│   ├── function.py
│   ├── requirements.txt
│   └── README.md
│
└── main/
    ├── fetch_device_readings.py
    ├── requirements.txt
    └── README.md

Each subdirectory represents an **individual Lambda function**, containing:
- ✅ Source code (`function.py`)
- 📦 Dependencies (`requirements.txt`)
- 📘 Documentation (`README.md`)

---

## ⚙️ Current Functions

### 🔍 Fetch Device Readings

<Callout type="info" title="Purpose">
Retrieves the latest sensor readings for a specific device from a DynamoDB table.
</Callout>

- **File:** `main/fetch_device_readings.py`
- **Input:** API Gateway event with a `device_id` in query parameters
- **Output:** JSON containing:
  - Most recent readings per sensor type
  - Associated metadata (unit, timestamp, device name)

<CodeBlock language="python">
{`
def lambda_handler(event, context):
    # Extract device_id
    device_id = event["queryStringParameters"].get("device_id")
    # Query DynamoDB and consolidate results
    ...
    return {
        "statusCode": 200,
        "body": json.dumps(result)
    }
`}
</CodeBlock>

---

## 📦 Prerequisites

Before running or deploying any function, ensure the following are installed/configured:

- 🐍 Python `3.8+`
- ☁️ AWS CLI (configured with proper IAM permissions)
- 📚 `boto3` installed for AWS integration:

```bash
pip install boto3
