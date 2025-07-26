# 🚀 AWS Lambda Functions

This repository contains a collection of **AWS Lambda functions** written in **Python**, designed to perform a variety of serverless tasks. These functions interact with AWS services such as **DynamoDB**, **API Gateway**, and more.

---

## 📁 Repository Structure

```
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
```

Each subdirectory represents an **individual Lambda function**, containing:
- ✅ Source code (`function.py`)
- 📦 Dependencies (`requirements.txt`)
- 📘 Documentation (`README.md`)

---

## ⚙️ Current Functions

### 🔍 Fetch Device Readings

**Purpose**: Retrieves the latest sensor readings for a specific device from a DynamoDB table.

- **File:** `main/fetch_device_readings.py`
- **Input:** API Gateway event with a `device_id` in query parameters
- **Output:** JSON containing:
  - Most recent readings per sensor type
  - Associated metadata (unit, timestamp, device name)

```python
def lambda_handler(event, context):
    # Extract device_id
    device_id = event["queryStringParameters"].get("device_id")
    # Query DynamoDB and consolidate results
    ...
    return {
        "statusCode": 200,
        "body": json.dumps(result)
    }
```

---

## 📦 Prerequisites

Before running or deploying any function, ensure the following are installed/configured:

- 🐍 Python `3.8+`
- ☁️ AWS CLI (configured with proper IAM permissions)
- 📚 `boto3` installed for AWS integration:

```bash
pip install boto3
```

---

## 🛠️ Setup & Deployment

Follow these steps to install dependencies and deploy a Lambda function:

### 1. Clone the Repository

```bash
git clone https://github.com/bluRib/aws-lambda-functions.git
cd aws-lambda-functions
```

### 2. Navigate to a Function Directory

```bash
cd main
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Deploy the Function

```bash
zip function.zip fetch_device_readings.py
aws lambda create-function \
  --function-name fetchDeviceReadings \
  --runtime python3.8 \
  --role <execution-role-arn> \
  --handler fetch_device_readings.lambda_handler \
  --zip-file fileb://function.zip
```

---

## ➕ Adding New Functions

Each new function should:
- Be placed in its own subdirectory
- Contain:
  - `function.py` (logic)
  - `requirements.txt` (dependencies)
  - `README.md` (usage)

Use existing functions as templates!

---

## 🤝 Contributing

Contributions are **welcome and appreciated**!

If you’d like to add a new Lambda function or improve an existing one:
1. Fork this repository
2. Create a feature branch
3. Submit a pull request

Ensure that:
- Your code matches the existing structure
- Includes documentation
- Follows Pythonic conventions

---

## 📄 License

Licensed under the **MIT License**.  
See [`LICENSE`](./LICENSE) for full details.
