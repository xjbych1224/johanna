[![Build Status](https://travis-ci.org/HardBoiledSmith/johanna.svg?branch=master)](https://travis-ci.org/HardBoiledSmith/johanna)

# Introduction

Johanna is a collection of boilerplate Python scripts that can do provisioning/deprovisioning of a simple backend system using AWS.

The backend includes below:
- VPC with two public subnets, two private subnets, routing tables, an internet gateway, a nat gateway and an EIP.
- IAM roles for Elastic Beanstalk
- EC2 key pair (SSH key)
- An Elastic Beanstalk application and an environment for Python Django API server
- An aurora RDS cluster with instances
- An sample SQS

You can do provisioning/deprovisioning/reprovisioning of the whole system or partial at once. Especially, the reprovisioning of Django API server means a '[continuous deployement](https://en.wikipedia.org/wiki/Continuous_delivery#Relationship_to_continuous_deployment)'.

# How To Play

Using [Lili](https://github.com/HardBoiledSmith/lili)(Vagrant provisioning script) is the simplest way to get a playground.

- Follow Lili [README manual](https://github.com/addnull/lili/blob/master/README.md)
- On Vagrant VM (Ubuntu 16.04)
  1. `sudo su`

  2. `cd /opt/johanna`

  3. Execute `conf.py` to configure your aws environment.

     ```bash
     ./conf.py --email YOUR_EMAIL --keypairname YOUR_AWS_KEYPAIR_NAME --accesskey YOUR_AWS_ACCESSKEY --secretkey YOUR_AWS_SECRETKEY --region AWS_REGION_NAME --az1 AVAILABILITY_ZONE_1 --az2 AVAILABILITY_ZONE_2 --template TEMPLATE_GIT_URL --user DB_USER --pw DB_PASSWORD
     ```

     *[Example]*

     ```bash
     ./conf.py --email ... --keypairname ... --accesskey ... --secretkey ... --region ap-northeast-2 --az1 ap-northeast-2a --az2 ap-northeast-2c --template git@github.com:HardBoiledSmith/kerrigan.git --user db-user --pw db-password
     ```

  4. `./run.py`

You can use this on web GUI

* [raynor](https://github.com/HardBoiledSmith/raynor) is web based GUI for johanna

# Notes

* If you use AWS IAM user credential instead of master account, it must have IAMFullAccess, AWSElasticBeanstalkFullAccess and PowerUserAccess permissions.

	![alt text](https://github.com/HardBoiledSmith/johanna/raw/master/docs/images/iam_user_permissions.png "IAM user permissions")

# Links

* [PyCon APAC 2016](https://www.pycon.kr/2016apac/program/15)
* [Slideshare](http://www.slideshare.net/addnull/daily-continuous-deployment-custom-cli-aws-elastic-beanstalk-64946800)
