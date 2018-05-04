### Docker-Based AWS Amplify Development Setup

This repository is an example starting point for an application built
using AWS Amplify.

The application has two parts:

1. A React frontend application (in frontend/), generated using
create-react-app, and run in development with Docker.

2. A backend of AWS Lambda Functions (in backend/), with an example
'hello world' function.

### AWS Service Stubs for Development

The backend runs using aws-sam-local for development.

Additionally, the docker-compose.yml file will start a copy of
Localstack with the following services:

Using Localstack:
- DynamoDB
- DynamoDB Streams
- Elasticsearch
- S3
- SNS
- SQS
- SES

Using moto:
- Congito Identity Pools

Each of these is exposed on a different port. Other localstack services
can be enabled by modifying the SERVICES env var in docker-compose.yml.

### Usage Notes

Usage Notes:

1. At this time, adjustments to the template.yaml file in backend/ may
  require restarting the docker image.

#### Cognito User Pools

The React application in /frontend already has the AWS Amplify JS library
included. There is a stub call to Amplify.config() to allow you to specify
an AWS Cognito User Pool for app authentication.

Note that currently there is no stub service for the Cognito User Pools, so
you will need to actaully create a User Pool to use Amplify's authentication.

Additionally, note that the [amplify CLI](https://aws.amazon.com/blogs/mobile/announcing-aws-amplify-and-the-aws-mobile-cli/)
defaults to (a) requiring a phone number and (b) turning on mandatory 2fa, and
that these settings are _not_ mutable on a Cognito User Pool.

As such, I recommend not using the Amplify CLI and instead creating a Cognito
User Pool by hand through the AWS Admin Dashboard.

Quick tip: Note that when creating a Cognito User Pool and adding a Client App
(which will give you the 'userPoolWebClientId' parameter for the Auth hash), you
will want to **uncheck** the default 'Generate Client Secret' box. The JavaScript
AWS SDK does not support the 'Client Secret Key'.

### Acknowledgemenets

Thank you to Xevo, Inc for the xevo/aws-sam-local docker image, and to
the localstack project.

### Next Steps

Further Development:

- In order to fully develop locally, it would be necessary to have a local
  implementation of AWS Cognito User Pools as well.

