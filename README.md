# Webhook Lambda Function

This AWS Lambda function receives webhook data from the myDevices platform and writes the parsed payload into a DynamoDB table. It enables real-time ingestion and storage of IoT sensor data for monitoring and analysis.

## Features

- Handles incoming HTTP POST requests from myDevices webhooks
- Extracts relevant sensor data (temperature, humidity, probe readings, battery, etc.)
- Writes structured data to an Amazon DynamoDB table
- Logs raw events for debugging and auditing

## Technologies Used

- AWS Lambda
- Amazon DynamoDB
- Python 3.x
- Boto3 (AWS SDK for Python)
- AWS API Gateway (for webhook integration)

## Deployment

1. Create a Lambda function in the AWS Console or via CLI
2. Attach permissions for DynamoDB (e.g., `PutItem` on your table)
3. Deploy the function code
4. Set up an API Gateway endpoint to trigger this function
5. Point your myDevices webhook to the API Gateway endpoint

## Environment Variables

Make sure to set the following in your Lambda environment configuration:

- `AWS_REGION` – AWS region where your DynamoDB table resides
- `TABLE_NAME` – Name of the DynamoDB table

## Example Payload

```json
{
  "name": "Temperature Sensor",
  "device_type": "LHT65N",
  "sensor_use": "Fridge",
  "temperature": 4.2,
  "humidity": 55,
  "battery": 100,
  "timestamp": "2025-07-07T14:32:00Z"
}
