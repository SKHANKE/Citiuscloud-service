Application Layer Deployment (Step-by-Step)

Step 1: Infrastructure Setup
I provisioned a VPC with public and private subnets, an Internet Gateway, a NAT Gateway, route tables, and security groups using Terraform.

Step 2: EC2 Deployment
I launched an EC2 instance in a private subnet to ensure it is not directly exposed to the internet.

Step 3: IAM Role Configuration
I created an IAM role and attached it to the EC2 instance to securely grant required permissions.

Step 4: SSL Certificate Setup
I imported a domain SSL certificate into AWS Certificate Manager to enable secure HTTPS communication.

Step 5: Application Load Balancer
I created an internet-facing Application Load Balancer, configured a target group, and set up HTTPS listener rules to route traffic securely.

Step 6: Target Group Configuration
I configured a target group on port 80 and attached it to an Auto Scaling group to distribute incoming traffic across EC2 instances.

Step 7: Listener Rule Configuration
I created HTTPS listener rules and associated them with the target group for proper traffic routing.

Step 8: ALB Security Group
I configured a security group for the Application Load Balancer to allow inbound HTTPS (port 443) traffic.

Step 9: EC2 Security Group
I updated the EC2 security group to allow inbound HTTP (port 80) traffic only from the ALB security group, ensuring secure internal communication.

Step 10: Launch Template
I created a launch template to define the configuration for EC2 instances used in the Auto Scaling group.

Step 11: Auto Scaling Group
I configured an Auto Scaling group with minimum, maximum, and desired capacity set to 2, attached the launch template, associated it with the Application Load Balancer, and deployed it across two private subnets.

Step 12: Scaling Behavior
The Auto Scaling group automatically maintains the desired capacity by scaling instances as needed.

Step 13: Secure Application Access
When accessing the domain, the application is served securely over HTTPS through the Application Load Balancer.
 
