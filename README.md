# My custom SAM pipeline template with one stage

This is a fork of the AWS repository: <https://github.com/aws/aws-sam-cli-pipeline-init-templates>

When you execute `sam pipeline init` you can choose the following:

> Select a pipeline template to get started:
> 1 - AWS Quick Start Pipeline Templates
> 2 - Custom Pipeline Template Location

However, option 1 creates a pipeline with 2 stages, and **I want to create only one stage**, so I forked the original repository and create my custom template.

To work with the AWS CLI `sam pipeline init` with the custom template I had to clean the project and left in the main folder the specific template that I want to execute.

Here I have the article that I wrote in my blog where I use this template to create my CI/CD pipeline with AWS CodePipeline: <https://www.playingaws.com/posts/how-to-create-serverless-applications-with-sam>

Log execution of the `sam pipeline init` with my custom template:

``` console
> sam pipeline init

sam pipeline init generates a pipeline configuration file that your CI/CD system
can use to deploy serverless applications using AWS SAM.
We will guide you through the process to bootstrap resources for each stage,
then walk through the details necessary for creating the pipeline config file.

Please ensure you are in the root folder of your SAM application before you begin.

Select a pipeline template to get started:
 1 - AWS Quick Start Pipeline Templates
 2 - Custom Pipeline Template Location
Choice: > 2
Template Git location: > https://github.com/alazaroc/aws-sam-cli-pipeline-init-templates.git

Cloning from https://github.com/alazaroc/aws-sam-cli-pipeline-init-templates.git (process may take a moment)
You are using the 1-stage pipeline template.
 _________
|         |
| Stage 1 |
|_________|

Checking for existing stages...

What is the Git provider?
 1 - Bitbucket
 2 - CodeCommit
 3 - GitHub
 4 - GitHubEnterpriseServer
Choice []: > 3
What is the full repository id (Example: some-user/my-repo)?: > alazaroc/aws-sam-app
What is the Git branch used for production deployments? [main]: >
What is the template file path? [template.yaml]: >
We use the stage name to automatically retrieve the bootstrapped resources created when you ran `sam pipeline bootstrap`.

Here are the stage configuration names detected in .aws-sam/pipeline/pipelineconfig.toml:
 1 - test
What is the name of stage 1 (as provided during the bootstrapping)?
Select an index or enter the stage name: > 1
What is the sam application stack name for stage 1? [sam-app]: >
Stage 1 configured successfully (you only have one stage).

To deploy this template and connect to the main git branch, run this against the leading account:
`sam deploy -t codepipeline.yaml --stack-name <stack-name> --capabilities=CAPABILITY_IAM`.
SUMMARY
We will generate a pipeline config file based on the following information:
 What is the Git provider?: GitHub
 What is the full repository id (Example: some-user/my-repo)?: alazaroc/aws-sam-app
 What is the Git branch used for production deployments?: main
 What is the template file path?: template.yaml
 What is the name of stage 1 (as provided during the bootstrapping)?
Select an index or enter the stage name: 1
 What is the sam application stack name for stage 1?: sam-app
 What is the pipeline execution role ARN for stage 1?: arn:aws:iam::xxxxxxxxxxxx:role/aws-sam-cli-managed-test-pip-PipelineExecutionRole-1RT9YMZ60U7L8
 What is the CloudFormation execution role ARN for stage 1?: arn:aws:iam::xxxxxxxxxxxx:role/aws-sam-cli-managed-test-CloudFormationExecutionR-FA52519RHRDD
 What is the S3 bucket name for artifacts for stage 1?: aws-sam-cli-managed-test-pipeline-artifactsbucket-jf6hixn3rx29
 What is the ECR repository URI for stage 1?:
 What is the AWS region for stage 1?: eu-west-1
Successfully created the pipeline configuration file(s):
 - codepipeline.yaml
 - assume-role.sh
 - pipeline/buildspec_unit_test.yml
 - pipeline/buildspec_build_package.yml
 - pipeline/buildspec_integration_test.yml
 - pipeline/buildspec_feature.yml
 - pipeline/buildspec_deploy.yml
```
