# Secure-website-hosting-in-AWS-with-VPC

## Project explanation
This is a project for launching a database-driven PHP website. The project's starting point is a modest PHP website and a database server that must be configured for maximum security. To address these concerns, I created infrastructure using custom VPCs and security groups that ensure optimum security.

Two public subnets and one private subnet are setup in the VPC. The public subnet hosts the PHP website and the bastion server, while the private subnet hosts the database instance. The public subnet is routed to the Internet gateway via Route 53 using route tables, making the site publicly accessible to the outside world. Even though the database instance is on a private subnet, it requires internet communication. NAT gateway is set to map private IP address to public address on the way out and vice versa on the way in for the same reason. So, using the route table, I've set up private routing to the NAT gateway. The NAT gateway with the elastic IP will communicate with the IGW via Route 53 to the outside world, receive the results, and then reroute to the database instance.

Implemented with restricted direct access to the website instance and the database instance to ensure maximum security for the instances. Here comes the role of the bastion server, which is configured with a security group that grants access to the website's admins and database creators. Only authorised users have access to the website and database instances from that bastion server. The website instance security group is likewise enabled with site-required ports and bastion server authorisation in the same way. Like before, the DB instance enabled the security group with the database need ports for the website and the bastion server authorisation.

## Architecture

![vpc](https://user-images.githubusercontent.com/65948438/167582719-39586778-2868-4b64-b240-6c2ac9336b18.jpeg)

## Features
  - High Security implemented infrastructure.
  - Easy configuration to implement.
  - Avoids data breaches by implementing an isolated space.

## Used Resources
  - VPC
  - Route 53
  - NAT Gateway
  - Route tables
  - Elastic IP
  - Internet Gateway
  - EC2 Instances
  - Security groups
  - Network Access Control List

## Conclusion
We spoke about how to host a website in a VPC with higher security in this tutorial. The goal is to increase website security, which we have achieved with this VPC setup. 

Thank you for your time !
