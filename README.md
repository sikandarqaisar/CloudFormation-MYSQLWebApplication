![Image](https://github.com/sikandarqaisar/CloudFormation-MYSQLWebApplication/blob/master/Untitled Diagram.png)
### STEP1:-
- Run VPC.yaml Stack.

#### Description: 
This stack create VPC with 2 Public Subnets and 1 Private Subnet. The private subnet can access the Internet by using a network address translation (NAT) gateway that resides in the public subnet. All Subnets are in Different Availability zones with their CIRDBlocks { (10.0.0.0/24)Subnet1, (10.0.2.0/24)Subnet2, (10.0.1.0/24)Subnet3 }. Then we have a Security Group. 1 for Load balancer 1 for PublicInstances 1 for Private Instance that we use in Other Stack. Then we have Output part that export values of Resources to use in other Stacks.

### STEP2:-
- Run instances.yaml Stack.

#### Description: 
Instance Stack create Private Instance in Private Subnet with Security Group. Its in Private Subnet so they have internet access through the public Subnet. 

### STEP3:-
- Run LB.yaml Stack 

#### Description:
In this stack we have AutoScalingGroup with LaunchConfiguration file. AutoScalingGroup create public instances in public subnets and they both are in different availability zone (we have 2 public subnets). Then we have Load Balancer which balance load between instances.

