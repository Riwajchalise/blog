---
layout: post
title: How to launch AWS’s EC2 instance using AWS CLI
author: riwaj
categories: [tech]
tags: [aws, ecc2, aws cli]
image: assets/images/2022-08-23/aws-cli-cover.jpg
description: This article discusses on how to launch AWS's ec2 instance using CLI in 3 easy  steps
featured: false
hidden: false
---  

Aws offers a command line interface tool that has a very wide scope. This blog article discusses on how we can launch a new ec2 instance using AWS CLI.

  

## Prerequisits

-   Have Aws cli setup in your device
    
-   Have a security group for you EC2 instance with port 22 enabled for ssh
    

  

## Steps

  

**Step 1:** Generate Key Pair

  KeyThe command below will help you generate a private key

  

- ```aws ec2 create-key-pair --key-name MyKey --query 'KeyMaterial' --output text > MyKey.pem```

  

Your private .pem file will be located in ```~/.aws``` in Linux and macOS and in Windows in ```%USERPROFILE%\.aws``` (c:/users/user_name/.aws) 

To verify that the key pair has been created write the following command
  

- ```aws ec2 describe-key-pairs```  
  

**Step 2:** Launch a Ec2 Instance

The command below will help you launch EC2 instance  

```aws ec2 run-instances --image-id ami-04ff9e9b51c1f62ca --count 1 --instance-type t2.micro --key-name MyKey --security-group-ids sg-075bab50c203dd121```

Syntax:

```{aws ec2 run-instances --image-id ami-xxxxxxxx --count 1 --instance-type t2.micro --key-name MyKeyPair --security-group-ids sg-xxxxxxxx --subnet-id subnet-xxxxxx}```  

Here is the description of the flags used in the command

*---image-id* : Id of the operating system that needs to be launched

*---count* : Number of instances to be launched

*---instance-type* : [Type of instance](https://aws.amazon.com/ec2/instance-types/) based on (processor, memory)

*---key-name*: Name of key used for authentication

*---security-group-ids*: Security Group controls as virtual firewall  

Make sure the security group has ssh enabled. If not the following command will do so (Optional)

```aws ec2 authorize-security-group-ingress --group-id sg-075bab50c203dd121 --protocol tcp --port 22 --cidr 0.0.0.0```

[Click here](https://docs.aws.amazon.com/cli/latest/userguide/cli-services-ec2-sg.html) to learn more about aws security group CLI.

If you donot assign any security group to the instance the default security group will be associated. Make sure it has port 22 open for ssh connection
  

**Step 3:** Ssh into your VPS

SSH into your server using the following command to access yout virtual  private server  (EC2 instance) 

Ssh -i ~/.aws/MyKey.pem username@ip

  
  

## Some additional commands

  

Describe instances

aws ec2 describe-instances

  

Creating tags for your instance

```aws ec2 create-tags --resources <instance if>--tags Key=Name,Value=MyInstance```

Terminating Instance

```aws ec2 terminate-instances --instance-ids <instance id>```

Deleting Keys

```aws ec2 delete-key-pair --key-name <keypairname>```


If you have any queries or you find anything concerning please comment below.