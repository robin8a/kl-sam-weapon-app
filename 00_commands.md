# SAM
## Init

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


# Build
```sh
# tell the command where your source code is if you get that error
sam build --base-dir hello_world
```

# package your application and deploy it to S3 using the package command:

```sh
sam package \
    --output-template-file packaged.yaml \
    --s3-bucket kl-sam-weapon-app-bucket

```

# Finally, run the deploy command:

```sh
sam deploy \
    --template-file packaged.yaml \
    --stack-name hello-world-app \
    --capabilities CAPABILITY_IAM \
    --region us-east-1
```











# Docker

```sh
docker run -v "$PWD":/var/task -it lambci/lambda:build-ruby2.5 /bin/bash \
-c "yum -y install mysql-devel ; bundle install --deployment ; bash"

Unable to find image 'lambci/lambda:build-ruby2.5' locally
build-ruby2.5: Pulling from lambci/lambda
a981bd693b45: Pull complete 
e2c11048af11: Pull complete 
0d9e356eba6a: Pull complete 
e25d09fd7c43: Pull complete 
Digest: sha256:25727c7b02478da32f5d104c00f7a8f3bb8084de37758a6372eee77e92e4d0b0
Status: Downloaded newer image for lambci/lambda:build-ruby2.5
Loaded plugins: ovl, priorities
amzn-main                                                                                                                               | 2.1 kB  00:00:00     
amzn-updates                                                                                                                            | 2.5 kB  00:00:00     
(1/5): amzn-main/latest/group_gz                                                                                                        | 4.4 kB  00:00:00     
(2/5): amzn-updates/latest/group_gz                                                                                                     | 4.4 kB  00:00:00     
(3/5): amzn-updates/latest/primary_db                                                                                                   | 3.1 MB  00:00:02     
(4/5): amzn-updates/latest/updateinfo                                                                                                   | 645 kB  00:00:06     
(5/5): amzn-main/latest/primary_db                                                                                                      | 4.0 MB  00:00:10     
Resolving Dependencies
--> Running transaction check
---> Package mysql-devel.noarch 0:5.5-1.6.amzn1 will be installed
--> Processing Dependency: mysql55-devel >= 5.5 for package: mysql-devel-5.5-1.6.amzn1.noarch
--> Processing Dependency: /usr/bin/mysql_config for package: mysql-devel-5.5-1.6.amzn1.noarch
--> Running transaction check
---> Package mysql55.x86_64 0:5.5.62-1.23.amzn1 will be installed
--> Processing Dependency: real-mysql55-libs(x86-64) = 5.5.62-1.23.amzn1 for package: mysql55-5.5.62-1.23.amzn1.x86_64
--> Processing Dependency: mysql-config for package: mysql55-5.5.62-1.23.amzn1.x86_64
---> Package mysql55-devel.x86_64 0:5.5.62-1.23.amzn1 will be installed
--> Running transaction check
---> Package mysql-config.x86_64 0:5.5.62-1.23.amzn1 will be installed
---> Package mysql55-libs.x86_64 0:5.5.62-1.23.amzn1 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================
 Package                                Arch                            Version                                    Repository                             Size
===============================================================================================================================================================
Installing:
 mysql-devel                            noarch                          5.5-1.6.amzn1                              amzn-main                             2.7 k
Installing for dependencies:
 mysql-config                           x86_64                          5.5.62-1.23.amzn1                          amzn-updates                           49 k
 mysql55                                x86_64                          5.5.62-1.23.amzn1                          amzn-updates                          7.5 M
 mysql55-devel                          x86_64                          5.5.62-1.23.amzn1                          amzn-updates                          201 k
 mysql55-libs                           x86_64                          5.5.62-1.23.amzn1                          amzn-updates                          816 k

Transaction Summary
===============================================================================================================================================================
Install  1 Package (+4 Dependent packages)

Total download size: 8.5 M
Installed size: 32 M
Downloading packages:
(1/5): mysql-devel-5.5-1.6.amzn1.noarch.rpm                                                                                             | 2.7 kB  00:00:00     
(2/5): mysql-config-5.5.62-1.23.amzn1.x86_64.rpm                                                                                        |  49 kB  00:00:00     
(3/5): mysql55-devel-5.5.62-1.23.amzn1.x86_64.rpm                                                                                       | 201 kB  00:00:01     
(4/5): mysql55-libs-5.5.62-1.23.amzn1.x86_64.rpm                                                                                        | 816 kB  00:00:03     
(5/5): mysql55-5.5.62-1.23.amzn1.x86_64.rpm                                                                                             | 7.5 MB  00:00:05     
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                          1.4 MB/s | 8.5 MB  00:00:06     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : mysql55-libs-5.5.62-1.23.amzn1.x86_64                                                                                                       1/5 
  Installing : mysql-config-5.5.62-1.23.amzn1.x86_64                                                                                                       2/5 
  Installing : mysql55-5.5.62-1.23.amzn1.x86_64                                                                                                            3/5 
  Installing : mysql55-devel-5.5.62-1.23.amzn1.x86_64                                                                                                      4/5 
  Installing : mysql-devel-5.5-1.6.amzn1.noarch                                                                                                            5/5 
  Verifying  : mysql-config-5.5.62-1.23.amzn1.x86_64                                                                                                       1/5 
  Verifying  : mysql55-5.5.62-1.23.amzn1.x86_64                                                                                                            2/5 
  Verifying  : mysql55-devel-5.5.62-1.23.amzn1.x86_64                                                                                                      3/5 
  Verifying  : mysql55-libs-5.5.62-1.23.amzn1.x86_64                                                                                                       4/5 
  Verifying  : mysql-devel-5.5-1.6.amzn1.noarch                                                                                                            5/5 

Installed:
  mysql-devel.noarch 0:5.5-1.6.amzn1                                                                                                                           

Dependency Installed:
  mysql-config.x86_64 0:5.5.62-1.23.amzn1 mysql55.x86_64 0:5.5.62-1.23.amzn1 mysql55-devel.x86_64 0:5.5.62-1.23.amzn1 mysql55-libs.x86_64 0:5.5.62-1.23.amzn1

Complete!
[DEPRECATED] The `--deployment` flag is deprecated because it relies on being remembered across bundler invocations, which bundler will no longer do in future versions. Instead please use `bundle config set deployment 'true'`, and stop using this flag
Don't run Bundler as root. Bundler can ask for sudo if it is needed, and installing your bundle as root will break this application for all non-root users on
this machine.
```

## So there we go. We need the file: libmysqlclient.so.18. How do we find it?
```sh
/sbin/ldconfig -p | grep mysql | cut -d\> -f2

/usr/lib64/mysql/libmysqlclient.so.18

mkdir lib
cp /usr/lib64/mysql/libmysqlclient.so.18 lib/

```

## Build

```sh
sam build --base-dir hello_world

```