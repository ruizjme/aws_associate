# AWS CLI

Create user with permissions "Programatic access". Use access keys through `aws configure`.

Get help with  `aws s3 help`.

For cli access from within AWS services, it is best to use **IAM roles** and not credentials. Roles can be managed from the console.

Roles can be attached to EC2 instances while running.

### S3

`aws s3 cp --recursive s3://bucket-name --region ap-southeast-2`

Region flags my need to be used to access content from s3 buckets across zones.

## Bootstrap scripts

Bash scripts can be run upon launching an instance. Scripts can be specified in the "user data" section when launching.

## Instance metadata

`curl http://169.254.169.254/latest/meta-data`
