# cloudformation-wordpress

The repo consists of cloudformation template files that could be used to create a wordpress web site with a given DNS name. Keeping modularity and maintainability, 3 files are created, 1 for each logical group of resources:
  1. Network stack (VPC, Subnet, SecurityGroup)
  2. Web app stack (EC2 instances, ELB, Wordpress installation using chef)
  3. Database stack (RDS)

Database stack and Web app stack are dependent on Network stack.

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

Considering that the templates and parameter-files are stored in S3, the cloud-formation stacks could be created using the following commands:
  1. aws cloudformation create-stack --stackname VpcSecurityGroupSubnetStack --template-body https://bucket-name.s3.amazonaws.com/wordpress_cf/database/VpcSecurityGroupSubnetStack.json --parameters https://bucket-name.s3.amazonaws.com/wordpress_cf/database/VpcSecurityGroupSubnetStack_params.json
  2. aws cloudformation create-stack --stackname DatabaseStack --template-body https://bucket-name.s3.amazonaws.com/wordpress_cf/database/DatabaseStack.json --parameters https://bucket-name.s3.amazonaws.com/wordpress_cf/database/DatabaseStack_params.json
  3. aws cloudformation create-stack --stackname WebAppStack --template-body https://bucket-name.s3.amazonaws.com/wordpress_cf/webapp/WebAppStack.json --parameters https://bucket-name.s3.amazonaws.com/wordpress_cf/webapp/WebAppStack_params.json
