# cloudformation-wordpress

The repo consists of cloudformation template files that could be used to create a wordpress web site with a given DNS name. Keeping modularity and maintainability, 3 files are created, 1 for each logical group of resources:
  1. Network stack (VPC and Subnet)
  2. Web app stack (EC2 instances, ELB, SecurityGroup)
  3. Database stack (RDS, SecurityGroup)

Database stack is dependent on Web app stack, which is in turn dependent on Network stack.

AMI support info:
  OS : Ubuntu 16.04 LTS
  Arch : HVM64
  Regions : {
            "us-east-1",
            "us-west-2",
            "us-west-1",
            "eu-west-1",
            "eu-west-2",
            "eu-west-3",
            "eu-central-1",
            "eu-north-1",
            "ap-northeast-1",
            "ap-northeast-2",
            "ap-northeast-3",
            "ap-southeast-1",
            "ap-southeast-2",
            "ap-south-1",
            "us-east-2",
            "ca-central-1",
            "sa-east-1"
            }

** Trying to run this template on any other "arch" type would result in "unsupported" error.
