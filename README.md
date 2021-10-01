I have created a new VPC with the IP range 10.0.0.0/16 which covers a wide range of possible IP addresses for the project. 
![VPC](https://user-images.githubusercontent.com/88770768/135626233-4f88f390-d2a7-4d2e-a334-d92354171fa1.JPG)

Within the VPC there is a public subnet which the EC2 instance runs in. This subnet has the IP range 10.0.0.0/24 which means that it is within the IP range of the VPC.
![Pub Sub](https://user-images.githubusercontent.com/88770768/135626605-734a24d3-d7dc-4dee-b15e-94a06ea2aed9.JPG)

The route table for this subnet contains a route to communicate with all IP addresses within the VPC and a route to an internet gateway.
![Public RT](https://user-images.githubusercontent.com/88770768/135626717-eb8af9ec-5f77-4ce8-bffe-69723e41e1a9.JPG)

The Security Group for the EC2 instance allows SSH connections through port 22 from any IP address, HTTP connections from ports 80 and 8080 and TCP connections from port 5000.
![EC2 Security group](https://user-images.githubusercontent.com/88770768/135626741-09356d41-9a4c-40a6-a7e8-0eab4bb8374b.JPG)

I have also created 2 private subnets within the VPC each with an IP range of 10.0.1.0/24 and 10.0.2.0/24 respectively.These subnets are used for the RDS instance and each of these subnets are in a different availability zone which allows for higher resiliency incase one AZ fails.
![Priv Sub](https://user-images.githubusercontent.com/88770768/135626783-0b9a9117-cc61-49e9-b77a-593cb8d5fb6d.JPG)

These subnets use a route table that only allows connections from any IP addresses within the VPC. This means that the private subnets can only be accessed from instances within the VPC. 
![Private RT](https://user-images.githubusercontent.com/88770768/135626808-9f9e0103-dc96-4316-a128-53125cf2e8f8.JPG)

The Security Group for the RDS instance is configured to allow MYSQL connections on port 3306 from any IP address and TCP connections from the IP address of the EC2 instance from port 5000
![RDS Security group](https://user-images.githubusercontent.com/88770768/135626830-5829291b-6e69-449e-8f65-5a4fdf551d7f.JPG)

After running the application the following output is diplayed on the IP of the EC2 instance on port 8080:
![Capture](https://user-images.githubusercontent.com/88770768/135625321-dbb4d623-90d8-4aad-bc07-729ada0d69ca.JPG)

