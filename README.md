# <p align="center">TASK DESCRIPTION </p>
# ``` Create a key pair```
# ``` Create a security group```
# ``` Launch an instance using the above created key pair and security group```
# ```Create an EBS volume and attach to the instance we created above```




# ` >> All the above steps must be performed using AWS CLI`

# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

# Let's Start:


![image](https://user-images.githubusercontent.com/61896468/95987763-7c8bc880-0e45-11eb-9049-f2778b3dd7b6.png)



##  Whether we use WebUI or CLI we need to login to AWS account, i.e., Authentication is a must. For this first create an IAM user, here I've provided AdministratorAccess to the user:

![image](https://user-images.githubusercontent.com/61896468/95985825-b5766e00-0e42-11eb-9dae-13dd9eb086d9.png) 

# *Now Install AWS CLI program according to your Operating System, here I installed AWS CLI version 2 for Windows.*

# To check whether the AWS CLI program installed properly or not, use this cmd:
# <p align="center">aws --version </p>


![image](https://user-images.githubusercontent.com/61896468/95985777-a2fc3480-0e42-11eb-92eb-966dd733b887.png) 

# Lets Authenticate to our AWS account using the IAM user we created, provide Access key, secret key & Region, using this cmd:

# <p align="center">aws configure</p>
![image](https://user-images.githubusercontent.com/61896468/95985735-8d870a80-0e42-11eb-8f86-f6d26559a7ae.png) 

# Creating a key pair: using this key pair only we can access our instance which we are going to launch further:

# <p align="center">aws ec2 create-key-pair --key-name newkey1 </p>
![image](https://user-images.githubusercontent.com/61896468/95985633-70523c00-0e42-11eb-8e2c-d0a8f5344baf.png)

![image](https://user-images.githubusercontent.com/61896468/95985674-7c3dfe00-0e42-11eb-90b3-f2fd45265f2d.png)
# Creating Security Group:

## It is basically Firewall security provided by AWS for the Instance to control Inbound & Outbound Traffic.
# <p align="center">  aws ec2 create-security-group --description "SSH protocol allowed" --group-name mySG    </p>

![image](https://user-images.githubusercontent.com/61896468/95985561-5c0e3f00-0e42-11eb-8453-3473f880adb9.png) 

# Allowing SSH protocol i.e., port 22, so that if we want we can connect to our Instance through SSH:
# <p align="center">  aws ec2 authorize-security-group-ingress --group-id sg-07a99fc6420e8b5a7 --protocol tcp --port 22 --cidr 0.0.0.0/0    </p>
![image](https://user-images.githubusercontent.com/61896468/95985462-413bca80-0e42-11eb-9e3c-036593d3b046.png)

![image](https://user-images.githubusercontent.com/61896468/95985486-4731ab80-0e42-11eb-8151-e22133e004d6.png)
# We can describe the Security group even from the CLI, using this cmd:
# <p align="center">aws ec2 describe-security-groups --group-id sg-07a99fc6420e8b5a7</p>

![image](https://user-images.githubusercontent.com/61896468/95985385-279a8300-0e42-11eb-9f42-27d3ee9197c7.png) 

# Launch EC2 Instance:

## ``Now we are ready to launch the EC2 Instance using the key pair & the security group we just created:``

# aws ec2 run-instances --security-group-ids sg-07a99fc6420e8b5a7 --instance-type t2.micro --count 1 --image-id ami-0e306788ff2473ccb --key-name newkey1

![image](https://user-images.githubusercontent.com/61896468/95985296-0e91d200-0e42-11eb-9097-128dd654cddc.png) 

# The instance is launched, we can confirm from either WebUI or CLI:

![image](https://user-images.githubusercontent.com/61896468/95985226-f752e480-0e41-11eb-9a61-c994593bbf0d.png) 

# Creating an EBS Volume:

# `Let's create 1GB EBS Volume which is like a Pendrive, then we will connect this volume to our Instance:`

# ``` aws ec2 create-volume --availability-zone ap-south-1a --volume-type gp2 --size 1```

![image](https://user-images.githubusercontent.com/61896468/95985158-e013f700-0e41-11eb-989e-c864fb755d4f.png) 

# Now we can see, our 1GB EBS volume is created & is available to be connected to any instance:

![image](https://user-images.githubusercontent.com/61896468/95985080-c4a8ec00-0e41-11eb-9cc0-78b0f7b9b42d.png) 

# *Attaching EBS Volume to the Instance:*

# ``` aws ec2 attach-volume --instance-id i-02d0cbde5b20b440a --volume-id vol-0a56a510b631f40fa --device /dev/sdh```

![image](https://user-images.githubusercontent.com/61896468/95985030-b064ef00-0e41-11eb-8c95-6377730a903e.png) 

# Now we can see that the 1GB EBS Volume is connected to our instance:
![image](https://user-images.githubusercontent.com/61896468/95984918-890e2200-0e41-11eb-9e76-847aff751237.png)

![image](https://user-images.githubusercontent.com/61896468/95984944-91fef380-0e41-11eb-99d4-a1fce403a9ed.png)


# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


#  <p align="center"> so finally i have completed `ARTH TASK 4/AWS CSA & DEVS TASK 1`,thanks a lot vimal sir and all the 24*7 working technical volunteers for all your seamless and thankful support  </p> 

