![DDT Framework Functional Testing - Pass](https://img.shields.io/badge/Testing%20|%20Functional%20%20-pass-green.svg?longCache=true&style=for-the-badge)<br>
![DDT Framework Functional Testing - Pass](https://img.shields.io/badge/Testing%20|%20Security%20%20%20-pass-green.svg?longCache=true&style=for-the-badge)<br>
# Log4j Vulnerability CVE-2021-44228 PoC

:biohazard::warning: | The software of the PoC which AWS Coudformation Template uses to build the software stack on the attacker machine is not included in this repo. The software is on an S3 bucket and you need **AccessKeyId** and **SecretAccessKey** to update in the CF template to be able to download it. You need sign an agreement to have access to the software. The purpose of this repo is to get you up and running quickly and help you as an organization to put proper controls to mitigate against all RCE (Remote Code Execution) attacks. This is not intended to teach you how to hack or help you to gain unauthorized access to systems you don't own. | :biohazard::warning:
:---: | :--- | :---


## Overview

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/01-CVE-2021-44228-log4jshell-overview-adam-alinsky.png?raw=true)

The Apache Log4j 2 utility is a Java-based logging utility commonly used for logging API/Web requests. On December 9th, 2021, a vulnerability (CVE-2021-44228) was reported that could allow a system running Apache Log4j 2 version 2.14.1 or below to be compromised.

This repository was created with the purpose to make it easy for organizations and individuals to study and research log4jshell vulnerability code name CVE-2021-44228.

The PoC environments would be built on AWS using CloudFormation. AWS CloudFormation is an infrastructure as code (IaC) service that allows you to easily model, provision, and manage AWS and third-party resources (Load balancers, Servers, routers, NAT Gateways, etc.).
<br><br>
![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/log4j-CVE-2021-44228-Architecture-v1.png?raw=true)

## 1. Read the article at my blog
Before you go any further, it is better to go through the article I published on Linkedin titled [DX: How to setup a PoC environment to study log4j vulnerability and protect your own Apps - Part I](https://www.earth2.digital/blog/log4j-CVE-2021-44228-how-to-setup-poc-adam-alinsky.html)

## 2. Get an AWS account
You need the to have the following:
1. Enough permission to run CloudFormation Template to create all the resorces needed.
2. You need a domain configured in Route53. You can buy a cheap one from inside Route53
 
## 3. Reach out to get access to the software and update the temaplte
At the begining of the template there are 2 parameters that must be set namely log4jShellAttackSFilesUserAccessKeyId and log4jShellAttackSFilesUserSecretAccessKey. Without setting these parameters, the CloudFormation template won't be able to access the software to build the software stacks required.

Message me on linkedin at https://au.linkedin.com/in/adamalinsky/

## 4. Run the template

You have 2 options to run the CloudFormation Template. Run it in one click by clicking on [this](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=aws-log4jshell-CVE-2021-44228-PoC&templateURL=https://s3.ap-southeast-2.amazonaws.com/myprototype.com.au/aws-log4jshell-CVE-2021-44228-poc.yaml) or follow the instructions below to run it manually.
1. Click "Create Stack"

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/01-CF.png?raw=true)

2. Upload CloudFormation Template

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/02-CF.png?raw=true)

3. After upload is successful, Click Next

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/03-CF.png?raw=true)

4. Specify Stack name

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/04-CF.png?raw=true)

5. After you receive your log4jShellAttackSFilesUserAccessKeyId and log4jShellAttackSFilesUserSecretAccessKey add their values.

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/05-CF.png?raw=true)

6. Select your HostedZone Resource for YourInfrastructure and Attacker Infrastructure.

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/051-CF.png?raw=true)

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/052-CF.png?raw=true)

7. Acknowledge IAM resources to be created and click "Create Stack"

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/06-CF.png?raw=true)

8. Wait a few minutes (around 7 minutes) for the stack to be created

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/07-CF.png?raw=true)

## 5. Access AppApi EC2 Instance as well as the Attacker Instance

Access is only allowed from the console using AWS Session Manager due to the following benefits:
- No Need for SSH keys or a bastion host.
- Sessions are secured using an AWS Key Management Service key.

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/08-connect-to-ec2-instance.png?raw=true)

![alt text](https://github.com/adamtheapiguy/log4jshellPoC/blob/main/media-assets/09-connect-to-ec2-instance.png?raw=true)

## log4jShell Demo Video

[![Log4jShell Demo](https://img.youtube.com/vi/ol5eiFGly4I/0.jpg)](http://www.youtube.com/watch?v=ol5eiFGly4I "Click to Play On YouTube.com")


