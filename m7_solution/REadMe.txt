(1)Dynamically increase the instances
-Using terraform loop - Count and for_each

Resources to loop
-primary resources
*aws_subnets - count loop
*aws_instance - count loop
*aws_s3_bucket - for_each

Impacted resources as a result of changes in the config above
-aws_route_table_association
-aws_lb_target_group_attachment

(2)using functions to meet more requirements
To move the startup script to a seperate file
- templatefile(file_location, {map of variables})

simplify the networking by determing the subnet address Dynamically
Ectract subnet address from VPC CIDR
- cidrsubnet(cidr_range, subnet bits to add, network number)

To consistently name all of the resources
Add tags to common tags
- merge(common_tags, {map of additional tags})

-s3 bucket name
lower(bucket_name)

