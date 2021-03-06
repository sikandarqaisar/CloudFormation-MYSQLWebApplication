# MYSQL_WebApplication.

### Description:
A WEB application that performs basic Create and Read operations. Using the AWS platform, the whole infrastructure instructions are written in YAML format in the form of nested stacks. Properly parameterized and mapped, all the stacks can be run in any Region on the AWS platform for the purpose of testing and further development.



<img src= "https://github.com/sikandarqaisar/CloudFormation-MYSQLWebApplication/blob/master/image.jpg" width="600" height="600">



### VPC Stack:
~~~
Upload VPC.yaml Stack.
~~~

**Description:**
This stack create VPC with 2 Public Subnets and 1 Private Subnet. The private subnet can access the Internet by using a network address translation (NAT) gateway that resides in the public subnet. All Subnets are in Different Availability zones with their CIRDBlocks { (10.0.0.0/24)Subnet1, (10.0.2.0/24)Subnet2, (10.0.1.0/24)Subnet3 }. Then we have a Security Group. 1 for Load balancer 1 for PublicInstances 1 for Private Instance that we use in Other Stack. Then we have Output part that export values of Resources to use in other Stacks.



### Instance Stack:
~~~
Upload instances.yaml Stack.
~~~

**Description:**
Instance Stack create Private Instance in Private Subnet with Security Group. Its in Private Subnet so they have internet access through the public Subnet.



### Load Balancer Stack:
~~~
Upload LoadBalancer.yaml Stack
~~~

**Description:**
In this stack we have AutoScalingGroup with LaunchConfiguration file. AutoScalingGroup create public instances in public subnets and private instance in private subnet as per thier availability zones. Then we have Load Balancer which balance load between instances.
