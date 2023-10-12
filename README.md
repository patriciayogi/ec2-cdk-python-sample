# Welcome to your CDK TypeScript template project

Deploy a Python web application to an EC2 instance running Nginx and uWSGI, using a CI/CD Pipeline created with Amazon CDK.

## Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `cdk deploy`      deploy this stack to your default AWS account/region
* `cdk diff`        compare deployed stack with current state
* `cdk synth`       emits the synthesized CloudFormation template

## Prerequisites
- AWS account: https://aws.amazon.com/getting-started/guides/setup-environment/
- AWS Cli: https://aws.amazon.com/getting-started/guides/setup-environment/module-three/

# Steps

## 1. Install CDK 

* npm install -g aws-cdk

## 2. Setting up GitHub

### Option 1(Deploying the existing sample-python-web-app  project)

* Get secret from github: https://github.com/patriciayogi/python-web-app-sample
  or create a new key(don't forget to update oauthToken in lib/ec2-cdk-stack)
* aws secretsmanager create-secret --name github-oauth-token --description "Github access token for cdk" --secret-string [GITHUB_ACCESS_TOKEN] --region REGION

### Option 2(Fork the sample application to your own GitHub account)

* fork the sample app: https://github.com/build-on-aws/sample-python-web-app
* aws secretsmanager create-secret --name github-oauth-token --description "Github access token for cdk" --secret-string [GITHUB_ACCESS_TOKEN] --region REGION
* update oauthToken and owner in lib/ec2-cdk-stack.ts file

## 3. Bootstrap

* cdk bootstrap

## 4. Deploy the structure

* cdk deploy
* you can use the outputs at the bottom that indicate the IP address of your web server: Look for Output-> Ec2CdkStack.IPAddress

## 5. Verify

* http://[IP]/# or EC2 instance name: http://ec2-[3-145-36-230].[us-east-2].compute.amazonaws.com/
* to check the status of the deployment, head over to the AWS CodePipeline console and find the python-webApp pipeline. 


## 6. Destroy

To avoid monthly changes:
* cdk destroy

https://community.aws/tutorials/using-ec2-userdata-to-bootstrap-python-web-app#cleaning-up-your-aws-environment
