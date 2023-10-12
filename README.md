# Welcome to your CDK TypeScript template project

Deploy a Python web application to an EC2 instance running Nginx and uWSGI, using a CI/CD Pipeline created with Amazon CDK.

## Setting up the CDK project

* npm install -g aws-cdk

## Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `cdk deploy`      deploy this stack to your default AWS account/region
* `cdk diff`        compare deployed stack with current state
* `cdk synth`       emits the synthesized CloudFormation template


## Setting up GitHub

### Option 1(Deploying the existing sample-python-web-app  project)

* Get secret from github: https://github.com/patriciayogi/sample-python-web-app 
  or create a new key(don't forget to update oauthToken in lib/ec2-cdk-stack)
* aws secretsmanager create-secret --name github-oauth-token --description "Github access token for cdk" --secret-string [GITHUB_ACCESS_TOKEN] --region REGION


### Option 2(Fork the sample application to your own GitHub account)

* fork the sample app: https://github.com/build-on-aws/sample-python-web-app
* aws secretsmanager create-secret --name github-oauth-token --description "Github access token for cdk" --secret-string [GITHUB_ACCESS_TOKEN] --region REGION
* update oauthToken and owner in lib/ec2-cdk-stack.ts file
