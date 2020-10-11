# cloudformation-wordpress

The repo consists of cloudformation template files that could be used to create a wordpress web site with a given DNS name. Keeping modularity and maintainability, 3 files are created, 1 for each logical group of resources:
  1. Network stack (VPC and Subnet)
  2. Web app stack (EC2 instances, ELB, SecurityGroup)
  3. Database stack (RDS, SecurityGroup)
Database stack is dependent on Web app stack, which is in turn dependent on Network stack.
