
# Init

```sh
sam init --runtime ruby2.5 --name kl-sam-weapon-app
cd kl-sam-weapon-app
```
# S3 Bucket
```sh
aws s3 mb s3://kl-sam-weapon-app-bucket
aws s3 ls | grep kl-sam*

```

# rvm

```sh
rvm help
rvm list
rvm use ruby-2.5.3

```

# Git

```sh
# github description: AWS :Serverless, SAM, Aurora Serverles, SPA

git init
git add .
git ci -m "Initial commit"
git remote add origin https://github.com/robin8a/kl-sam-weapon-app.git
git push -u origin master
```

# SAM
## Build
```sh
sam build

### Result
sam build
Building resource 'HelloWorldFunction'
Running RubyBundlerBuilder:CopySource
Running RubyBundlerBuilder:RubyBundle
Running RubyBundlerBuilder:RubyBundleDeployment

Build Succeeded

Built Artifacts  : .aws-sam/build
Built Template   : .aws-sam/build/template.yaml

Commands you can use next
=========================
[*] Invoke Function: sam local invoke
[*] Deploy: sam deploy --guided
```

## Deploy

```sh
sam deploy --guided

### result
sam deploy --guided

Configuring SAM deploy
======================

        Looking for samconfig.toml :  Not found

        Setting default arguments for 'sam deploy'
        =========================================
        Stack Name [sam-app]: kl-sam-sam-weapon-app     
        AWS Region [us-east-1]: 
        #Shows you resources changes to be deployed and require a 'Y' to initiate deploy
        Confirm changes before deploy [y/N]: Y
        #SAM needs permission to be able to create roles to connect to the resources in your template
        Allow SAM CLI IAM role creation [Y/n]: Y
        HelloWorldFunction may not have authorization defined, Is this okay? [y/N]: y
        Save arguments to samconfig.toml [Y/n]: Y

        Looking for resources needed for deployment: Not found.
        Creating the required resources...
        Successfully created!

                Managed S3 bucket: aws-sam-cli-managed-default-samclisourcebucket-17wqdnkp2580z
                A different default S3 bucket can be set in samconfig.toml

        Saved arguments to config file
        Running 'sam deploy' for future deployments will use the parameters saved above.
        The above parameters can be changed by modifying samconfig.toml
        Learn more about samconfig.toml syntax at 
        https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-config.html

        Deploying with following values
        ===============================
        Stack name                 : kl-sam-sam-weapon-app
        Region                     : us-east-1
        Confirm changeset          : True
        Deployment s3 bucket       : aws-sam-cli-managed-default-samclisourcebucket-17wqdnkp2580z
        Capabilities               : ["CAPABILITY_IAM"]
        Parameter overrides        : {}

Initiating deployment
=====================
Uploading to kl-sam-sam-weapon-app/9f36d2f0295199bf0fd7bbc24027c493  546858 / 546858.0  (100.00%)
HelloWorldFunction may not have authorization defined.
Uploading to kl-sam-sam-weapon-app/48575a48b14bbf08af6ce27543857eac.template  1122 / 1122.0  (100.00%)

Waiting for changeset to be created..

CloudFormation stack changeset
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Operation                                                   LogicalResourceId                                           ResourceType                                              
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ Add                                                       HelloWorldFunctionHelloWorldPermissionProd                  AWS::Lambda::Permission                                   
+ Add                                                       HelloWorldFunctionRole                                      AWS::IAM::Role                                            
+ Add                                                       HelloWorldFunction                                          AWS::Lambda::Function                                     
+ Add                                                       ServerlessRestApiDeployment47fc2d5f9d                       AWS::ApiGateway::Deployment                               
+ Add                                                       ServerlessRestApiProdStage                                  AWS::ApiGateway::Stage                                    
+ Add                                                       ServerlessRestApi                                           AWS::ApiGateway::RestApi                                  
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Changeset created successfully. arn:aws:cloudformation:us-east-1:369939105943:changeSet/samcli-deploy1589577720/94b774a5-30d2-4e38-9faf-48238b915dc7


Previewing CloudFormation changeset before deployment
```