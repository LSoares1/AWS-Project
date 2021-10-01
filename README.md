I have created a new VPC with the IP range 10.0.0.0/16 which covers a wide range of possible IP addresses for the project 

Within the VPC there is a public subnet which the EC2 instance runs in. This subnet has the IP range 10.0.0.0/24 which means that it is within the IP range of the VPC. The route table for this subnet contains a route to communicate with all IP addresses within the VPC and a route to an internet gateway. The Security Group for the EC2 instance allows SSH connections through port 22 from any IP address, HTTP connections from ports 80 and 8080 and TCP connections from port 5000.

I have also created 2 private subnets within the VPC each with an IP range of 10.0.1.0/24 and 10.0.2.0/24 respectively. These subnets are used for the RDS instance and each of these subnets are in a different availability zone which allows for higher resiliency incase one AZ fails. These subnets use a route table that only allows connections from any IP addresses within the VPC. This means that the private subnets can only be accessed from instances within the VPC. The Security Group for the RDS instance is configured to allow MYSQL connections on port 3306 from any IP address and TCP connections from the IP address of the EC2 instance from port 5000






