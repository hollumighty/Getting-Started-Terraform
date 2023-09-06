#Deliverables in in this update

From the previous update - Multi-Zone, Multi-instance application succesfully configured and deployed

REQUEST 
(1)Copy website content
*upload the website content to s3 bucket
-Log traffic to the s3 bucket
*Access to one of the dev teams to the load balancer for analysis and debugging
(2)Use specific provider versions 
So all team members can use the same version of terraform and provider pluggin
-properly formatted files
*terrafom files to be formatted consistently to help sharing accross the team

SOLUTION ARCHITECTURE
(1)We have an s3 bucket and upload the website contents
-using: s3 resources - aws_s3_bucket(to create the bucket), aws_s3_object(to add resources to the bucket)

assign the EC2 instances to have access to fetch information from the s3 bucket
-create: aws-iam_role(for the instances access bcos we don't want to make the access public)
-aws_iam_role_policy (grant the role permission to the bucket)
-aws_iam_instances_profile (attach the role to the intances)

we also grant the load balancer principal access to the s3 bucket to write files
-aws_s3_bucket_policy (grant the load balancer principal access)
-aws_elb_service_account (get load balander principal id)

*For the specific provider versions, use the terraform provider and preferred cloud provider and specify the version constraint.