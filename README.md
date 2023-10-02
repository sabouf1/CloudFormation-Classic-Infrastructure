# CloudFormation Classic Infrastructure

This repository contains AWS CloudFormation templates to create classic infrastructure components, including a Virtual Private Cloud (VPC), subnets, security groups, EC2 instances, and a DynamoDB table. These templates help you quickly set up a basic production-ready environment in your AWS account.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Resources](#resources)
- [License](#license)

## Prerequisites

Before you begin, make sure you have the following prerequisites in place:

- An AWS account with appropriate permissions to create the specified resources.
- AWS CLI installed and configured with the necessary credentials.

## Getting Started

Follow the steps below to deploy the infrastructure using AWS CloudFormation:

1. Clone this repository to your local machine or download the CloudFormation template file.
   
   ```shell
   git clone https://github.com/sabouf1/CloudFormation-Classic-Infrastructure.git
   ```

2. Deploy the CloudFormation stack using AWS CLI.

   ```shell
   aws cloudformation create-stack \
     --stack-name YourStackName \
     --template-body file://path/to/your/template.yaml \
     --parameters ParameterKey=KeyName,ParameterValue=YourKeyPairName \
     --capabilities CAPABILITY_NAMED_IAM
   ```

   Replace `YourStackName` with a unique name for your stack, `path/to/your/template.yaml` with the path to the downloaded template file, and `YourKeyPairName` with the name of your AWS Key Pair.

3. Monitor the stack creation progress using the AWS Management Console or AWS CLI.

Once the stack creation is complete, you'll have a production-ready infrastructure set up in your AWS account.

## Resources

### VPC Configuration
- `myVPC`: AWS VPC with a specified CIDR block, DNS support, and DNS hostnames enabled.

### Internet Gateway
- `myInternetGateway`: AWS Internet Gateway attached to the VPC.

### Route Table and Routes
- `myRouteTable`: AWS Route Table associated with the VPC.
- `myRoute`: Route in the route table to enable internet access via the Internet Gateway.

### Subnets
- `subnet1` and `subnet2`: Public subnets in Availability Zone `sa-east-1a`.
- `subnet3` and `subnet4`: Private subnets in Availability Zone `sa-east-1b`.

### NAT Gateway
- `NatGWEIP`: Elastic IP for the NAT Gateway.
- `NATGateway`: NAT Gateway for private subnets to access the internet.

### Security Groups
- `EC2SecurityGroup`: Security group allowing HTTP and SSH traffic.

### EC2 Instances
- `PublicEC2Instance`: Public EC2 instance in `subnet1`.
- `PrivateEC2Instance`: Private EC2 instance in `subnet2`.

### DynamoDB Table
- `MetroDBTable`: DynamoDB table named `metroddb` with provisioned capacity.

## License

This project is licensed under the [MIT License](LICENSE). Feel free to use and modify the templates as needed for your own AWS infrastructure.
