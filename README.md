# nestedstacks
Set of 1 parent stack with 3 nested stacks (rds, skeleton, app/ec2)

These template create:
- 1 VPC
- Bastion host (in autoscaling group)
- Autoscaling group with apache servers (2 AZ's, 2 private subnets)
- NAT gateway
- RDS cluster
- ALB 

Considerations:
- In this setup the RDS stack is a nested stack. If any change with the other stacks goes wrong you could easily corrupt your   precious data. If you're using this setup for production it's wise to create a seperate rds stack and use the import/export-   values functionality instead. If anything goes wrong you'll at least still have your unharmed database stack. Takes a lot     less time debugging too ;-) 

- No nACL's are configured. Please do so when using this template for any form of production environment! 

Stating the obvious:
- Please change the URL's in the Parent Stack to where ever you have placed your templates. 
- AMI is region specific so please check what AMI's are available in your region of choice.

