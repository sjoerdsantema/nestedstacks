# nestedstacks
Set of 1 parent stack with 3 nested stacks (rds, skeleton, app/ec2)

These nested templates create:
- VPC
- Bastion host (in autoscaling group)
- Autoscaling group with Apache webservers (2 az's, 2 private subnets)
  + Monitoring (mem-utilized) and Apache logs aggregation in Cloudwatch
  + Notifications through SNS on scale-ups, scale-downs or failure
- NAT gateway
- RDS cluster (multi-az)
- ALB 

Considerations:
- In this setup the RDS stack is a nested stack. If any change with the other stacks goes wrong you could easily corrupt your   precious data. If you're using this setup for production it's wise to create a seperate rds stack and use the import/export-   values functionality instead. If anything goes wrong you'll at least still have your unharmed database stack. Takes a lot     less time waiting for cfn stacks to build too ;-) 

- No nACL's are configured. Please do so when using this template for any form of production environment! 

Stating the obvious:
- Please change the URL's in the Parent Stack to where ever you have placed your templates. 
- AMI is region specific so please check what AMI's are available in your region of choice. Consider adding mapping for AMI's   per region.

