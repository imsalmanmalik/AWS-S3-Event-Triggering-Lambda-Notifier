# AWS S3 Event-Triggered Lambda Function and SNS Notifications

## Project Description

This project demonstrates an end-to-end flow of how to automatically process file uploads to an S3 bucket using an AWS Lambda function, and subsequently notify a user through email using Amazon Simple Notification Service (SNS). It is entirely automated by a shell script which creates the necessary resources and sets up the necessary permissions and triggers.

The project makes use of several AWS services including S3, Lambda, SNS, IAM, and STS, as well as third-party tools like `jq` for processing JSON data, and is written using Bash and Python scripting languages.

## Workflow

The project follows this flow:

1. A user uploads a file to an S3 bucket.<b>
2. This triggers an AWS Lambda function that is set to listen for the 'ObjectCreated' event from this specific S3 bucket.<b>
3. The Lambda function processes the event, then publishes a message to an SNS topic.<b>
4. An email is then sent to the subscribed email address containing the message from the SNS topic.<b>

This entire workflow is set up using a shell script which does the following:

1. Creates an IAM role for the Lambda function.<b>
2. Attaches necessary policies to the role.<b>
3. Creates the S3 bucket.<b>
4. Creates the Lambda function and uploads the Python script.<b>
5. Sets the Lambda function to be triggered by 'ObjectCreated' events from the S3 bucket.<b>
6. Creates the SNS topic.<b>
7. Subscribes an email address to the SNS topic.<b>

## Setup and Execution

To set up and execute this project, run the shell script `s3-notification-triggers.sh` from your terminal:

```bash
$ chmod +x ./s3-notification-triggers.sh
$ ./s3-notification-triggers.sh
```
Ensure that you have AWS CLI installed and configured with your AWS account credentials, and that you have 'jq' installed for processing JSON data.

## Screenshots
Two screenshots have been added to this repository to show the functioning of this project.

1. email_notification.png: This screenshot shows the email received when a new object was added to the S3 bucket.<b>
2. lambda_console.png: This screenshot shows the Lambda console with the function overview, displaying the trigger event with the S3 bucket.<b>
