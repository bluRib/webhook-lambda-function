AWS Lambda Functions

This repository contains a collection of AWS Lambda functions designed to handle various serverless tasks. Each function is implemented in Python and leverages AWS services such as DynamoDB, API Gateway, and more.

Repository Structure

The repository is organized as follows:

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


Each folder contains the code for a specific Lambda function, along with its dependencies and documentation.

Current Functions
Fetch Device Readings

File: fetch_device_readings.py

Description: This function retrieves the latest sensor readings for a specific device from a DynamoDB table. It processes API Gateway events, extracts the device_id from query parameters, and queries the table to fetch up to 50 of the most recent records. The function consolidates the data to return the latest reading for each sensor type, along with metadata such as the unit, timestamp, and device name.

Additional Functions

Additional Lambda functions will be added to this repository over time. Each function will include its own documentation and usage instructions.

Prerequisites

To use the functions in this repository, ensure you have the following:

Python 3.8 or later

AWS CLI configured with appropriate permissions

boto3 library installed for AWS service integration

Setup and Deployment
Clone the repository:
git clone https://github.com/bluRib/aws-lambda-functions.git
cd aws-lambda-functions

Navigate to the desired function directory:
cd main

Install dependencies:
pip install -r requirements.txt

Deploy the function using AWS CLI or your preferred deployment tool. For example:
aws lambda create-function \
    --function-name fetchDeviceReadings \
    --runtime python3.8 \
    --role <execution-role-arn> \
    --handler fetch_device_readings.lambda_handler \
    --zip-file fileb://function.zip

Contributing

Contributions are welcome. If you would like to add a new function or improve an existing one, please submit a pull request. Ensure your code follows the repository's structure and includes proper documentation.

License

This repository is licensed under the MIT License. See the LICENSE file for more details.
