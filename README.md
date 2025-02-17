# AWS Kendra Experience Automation

## Description
This project provides an automated way to deploy an Amazon Kendra search experience using AWS CloudFormation. It creates a Kendra index and search experience, with automatic user association through AWS IAM Identity Center (formerly AWS SSO).

## Features
- Automated deployment of Kendra index
- Creation of search experience interface
- Integration with AWS IAM Identity Center for user authentication
- Automatic user association and permission management
- Custom resource handling through AWS Lambda

## Prerequisites
- AWS Account with appropriate permissions
- AWS IAM Identity Center (formerly AWS SSO) enabled
- Python 3.9 or later
- AWS CLI configured with appropriate credentials
- User must exist in IAM Identity Center

## Quick Start
1. Clone this repository
2. Update the username in the Lambda function (default: 'pandasr')
3. Deploy the CloudFormation stack:
```bash
aws cloudformation create-stack \
  --stack-name kendra-search-experience \
  --template-body file://kendra-basic-stack.yaml \
  --capabilities CAPABILITY_IAM
```

## The CloudFormation template creates the following resources:

Amazon Kendra Index
Kendra Search Experience
IAM Roles and Policies
Lambda Function for Custom Resource
Custom Resource for Experience Management

## Configuration

Parameters - 
IndexName: Name of the Kendra Index (Default: MyKendraIndex)
ExperienceName: Name of the Search Experience (Default: MySearchExperience)

IAM Permissions - 
The stack creates three IAM roles:

KendraIndexRole: For Kendra index operations
CustomResourceRole: For Lambda function execution
KendraExperienceRole: For Kendra experience management

Lambda Function- 
The included Lambda function handles:
- User lookup in IAM Identity Center
- Experience creation and configuration
- User association and permission assignment
- Cleanup during stack deletion

## Troubleshooting
Common issues and solutions:
- User not found: Ensure the username in the Lambda function matches your IAM Identity Center username
- Permission errors: Verify IAM roles have correct policies attached
- Identity Center errors: Confirm Identity Center is enabled in your account

## Security Considerations
The template uses managed policies for simplicity but please ensure to implement granular controls based on your environment requirements 
Sensitive information should be stored in AWS Secrets Manager
Regular security audits are recommended

## Limitations
Currently supports single user association as this is just for sample purposes 
Requires IAM Identity Center setup
Uses Developer Edition of Kendra
Region-dependent deployment

## Contributing
Fork the repository
Create a feature branch
Commit your changes
Push to the branch
Create a Pull Request

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Support
For support, please open an issue in the GitHub repository.

## Disclaimer
This is not an official AWS project. Use at your own risk.

