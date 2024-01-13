# AWS CodeDeploy Setup Guide
This guide will walk you through the process of setting up an AWS CodeDeploy pipeline to deploy an application on an EC2 instance using S3 as the source. Follow these steps to ensure a smooth deployment process.

## Prerequisites
1. AWS Account: Ensure you have an AWS account with the necessary permissions to create and manage CodeDeploy, S3, and IAM resources.

2. EC2 Instance: Set up an EC2 instance where you want to deploy your application.

3. S3 Bucket: Create an S3 bucket to store your application artifacts.

3. IAM Role: Create an IAM role with the necessary permissions for CodeDeploy and EC2.

4. CodeDeploy Agent Setup on EC2 Instance
   
Use the following script to set up the CodeDeploy agent on your EC2 instance:

#!/bin/bash
```
sudo yum -y update
sudo yum -y install ruby
sudo yum -y install wget
cd /home/ec2-user
wget https://aws-codedeploy-us-east-2.s3.us-east-2.amazonaws.com/latest/install
sudo chmod +x ./install
sudo ./install auto
sudo yum install -y python-pip
sudo pip install awscli
```


## Application Setup
1. Create an Application: Use the AWS Management Console to create a new CodeDeploy application.

2. Download Application: Download your application code. For example, use the following command to download a sample application:

```
curl -O http://s3.amazonaws.com/aws-codedeploy-us-east-1/samples/latest/SampleApp_Linux.zip
```

3. Upload Application to S3: Upload your application code to the previously created S3 bucket.

## Pipeline Setup
1. Create a CodePipeline: Use the AWS Management Console to create a new CodePipeline.

2. Configure Source Stage:
- Choose S3 as the source provider.
- Select the S3 bucket and specify the application code location.
- Configure Build Stage (Optional): If you have a build process, configure this stage to build your application.

## Configure Deploy Stage:
1. Choose AWS CodeDeploy as the deployment provider.
2. Select the CodeDeploy application created earlier.
3. Configure the deployment group and any other necessary settings.
4. Review and Create Pipeline: Review your pipeline configuration and create the pipeline.

## Deploy Application
Once the pipeline is set up, it will automatically trigger when changes are made to the specified S3 bucket. Monitor the pipeline in the AWS Management Console to track the deployment progress.

This completes the setup of an AWS CodeDeploy pipeline to deploy an application on an EC2 instance using S3 as the source.
