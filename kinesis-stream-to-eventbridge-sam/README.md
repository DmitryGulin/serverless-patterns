# Amazon Kinesis Stream to Amazon EventBridge Bus using Amazon EventBridge Pipes
This pattern shows how to use EventBridge Pipes to publish events to custom Event Bus 
Learn more about this pattern at Serverless Land Patterns: https://serverlessland.com/patterns/serverless-patterns/kinesis-stream-to-eventbridge-sam

Important: this application uses various AWS services and there are costs associated with these services after the Free Tier usage - please see the [AWS Pricing page](https://aws.amazon.com/pricing/) for details. You are responsible for any AWS costs incurred. No warranty is implied in this example.

## Requirements
* [Create an AWS account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) if you do not already have one and log in. The IAM user that you use must have sufficient permissions to make necessary AWS service calls and manage AWS resources.
* [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) installed and configured
* [Git Installed](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* [AWS Serverless Application Model](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html) (AWS SAM) installed
## Deployment Instructions
1. Create a new directory, navigate to that directory in a terminal and clone the GitHub repository:
    ```bash 
    git clone https://github.com/aws-samples/serverless-patterns
    ```
1. Change directory to the pattern directory:
    ```bash
    cd kinesis-stream-to-eventbridge-sam
    ```
1. From the command line, use AWS SAM to deploy the AWS resources for the pattern as specified in the template.yml file:
    ```bash
    sam deploy --guided
    ```
1. During the prompts:
    * Enter a stack name
    * Enter the desired AWS Region
    * Enter an IAM role name for the parameter `IAMRoleName` 
    * Allow SAM CLI to create IAM roles with the required permissions
    Once you have run `sam deploy —guided` mode once and saved arguments to a configuration file (samconfig.toml), you can use `sam deploy` in future to use these defaults.
1. Note the outputs from the SAM deployment process. These contain the resource names and/or ARNs which are used for testing.


## How it works
Please refer to the architecture diagram below:
![End to End Architecture](architecture.png)

When data is sent to the Amazon Kinesis data stream, Amazon EventBridge Pipe consumes the data and sends them to an Amazon EventBridge custom Event Bus. 

## Testing

From the command line, please run the following command to send a single data record to the Kinesis data stream. Note that you must edit the <value> with the Kinesis data name that is deployed.
```bash
    aws kinesis put-record --stream-name <value> --data testdata --partition-key "test" 
 ```

## Cleanup
 
1. Delete the stack
    ```bash
    sam delete
    ```
----
Copyright 2023 Amazon.com, Inc. or its affiliates. All Rights Reserved.
SPDX-License-Identifier: MIT-0
