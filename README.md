# AWS-simple-secure-network
By implementing industry best practices and leveraging state-of-the-art security technologies, this project aims to establish a robust security framework that ensures the confidentiality, integrity, and availability of data stored and transmitted within the cloud infrastructure of a small business.

I. Proposed Architecture 
![image](https://github.com/MOUSSADOUNDA/AWS-simple-secure-network/assets/129728703/2ce24632-2e82-4944-89ab-0c7431dcd142)

Here is our Network topology with 4 VPCs located in Ohio, each VPC is a different Network. A transit gateway interconnects all the VPCs.
For this project we are going to use only the VPC1 which will run two EC2 instances
![image](https://github.com/MOUSSADOUNDA/AWS-simple-secure-network/assets/129728703/7c7a31ec-466f-4374-9127-6e72b44069b5)

The public subnet contains an EC2 instance that we consider as a web server, the internet gateway enables this instance to have access to the internet and people from the internet access the instance. This makes instances in the public subnet expose to cyber threat.
The private subnet contains an EC2 instance that we consider as a database. The instances in the private subnet are not accessible from the internet that is why it is more secure than the public subnet. However, the instance in the private subnet might need to access to the internet. This will be possible by using the NAT gateway that is in the public subnet, so the private instance will be routed to the internet gateway and access the internet.   

In the following sections we have tdone a brief description of steps of the work, the details will in the attached PDF.

II. Security Groups

AWS Security Groups are virtual firewalls that control inbound and outbound traffic for Amazon EC2 instances, allowing you to define rules to permit or deny traffic based on protocol, port, and source/destination IP addresses

III. Identity and Access Management (IAM)

Instead of assigning permissions to each user we have created a group called DevTeam so the permissions will be assigned to the group. This will make the management of the users easier.
![image](https://github.com/MOUSSADOUNDA/AWS-simple-secure-network/assets/129728703/cf8ffc01-b481-4194-816a-ba7dcbc0f60b)

IV. Remote Access to the instances

In order to have a remote access to the web server from our Ubuntu terminal we need the private key of the EC2 instance. To access the database, one of the most secure ways is by SSH forwarding also known as SSH bastion host.

V. Security Hardening

To harden the network we have implemented few best practices configuration for minimizing potential attack surfaces such as: SSH Connexion, Hide apache2 server banner, Disable Apache directory browsing.
