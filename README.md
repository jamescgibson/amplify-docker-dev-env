### Docker-Based AWS Amplify Development Setup

This repository is an example starting point for an application built
using AWS Amplify.

The application has two parts:

1. A React frontend application (in frontend/), generated using
create-react-app, and run in development with Docker.

2. A backend of AWS Lambda Functions (in backend/), with an example
'hello world' function.

The backend runs using aws-sam-local.

Additionally, the docker-compose.yml file will start a copy of
Localstack with the following services:

- DynamoDB
- DynamoDB Streams
- Elasticsearch
- S3
- SNS
- SQS
- SES

Each of these is exposed on a different port. Other localstack services
can be enabled by modifying the SERVICES env var in docker-compose.yml.

Usage Notes:

- At this time, adjustments to the template.yaml file in backend/ may
  require restarting the docker image.

Thank you to Xevo, Inc for the xevo/aws-sam-local docker image, and to
the localstack project.

Further Development:

In order to fully develop locally, it would be necessary to have a local
implementation of AWS Cognito as well.

