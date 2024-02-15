# aws-sandbox
Templates and scripts for experimenting with AWS features.

## Contents
* `cdk/` - AWS CDK (Typescript) stacks
* `templates/` - Cloudformation templates
* `stackparams/` - Parameter overrides to use with Cloudformation templates\

## Usage
### Set up VPC with two public and two private subnets
Specify a name and CIDR ranges in `stackparams/sandbox-vpc.json`. Then run:
```
aws cloudformation deploy --template-file templates/vpc-with-subnets.yml --parameter-overrides file://stackparams/sandbox-vpc.json --stack-name sandbox-vpc
```
### Set up basic webserver
```
aws cloudformation deploy --template-file templates/webserver.yml --parameter-overrides VPC=[VPC ID] Subnet=[Subnet ID] KeyName=aws-sandbox --stack-name webserver
```
### Set up phonebook app on multi-AZ EC2 cluster & RDS instance
Specify valid VPC and subnets in `stackparams/phoneapp.json`. Then run:
```
aws cloudformation deploy --template-file templates/webcluster.yml --parameter-overrides file://stackparams/phoneapp.json --stack-name phoneapp-web
```
Update `stackparams/phoneapp.json`, setting `IngressGroupID` to the EC2 security group ID after creating the `phoneapp-web` stack. The run:
```
aws cloudformation deploy --template-file templates/mysqlrds.yml --parameter-overrides file://stackparams/phoneapp.json --stack-name phoneapp-db
```

### Set up EKS cluster
Specify valid VPC and subnets in `stackparams/ekscluster.json`. Then run:
```
aws cloudformation deploy --template-file templates/ekscluster.yml --parameter-overrides file://stackparams/ekscluster.json --capabilities CAPABILITY_NAMED_IAM --stack-name sandbox-eks
```
