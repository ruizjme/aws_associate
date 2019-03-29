Data centers > IAAS (ec2) > PAAS (elastic beanstalk) > Containers (docker, ECS) > Serverless (lambda)

# Lambda

Lambda encapsulates all that is needed to run code.
No need to manage os, servers, patches, scaling.

**Event** driven (triggers) or HTTP **requests**.

Runtime can be C#, Go, Java, Node, Python.

### Triggers
* API gateway
* AWS iot
* slexa
* cloudfront
* cloudwatch
* kinesis
* s3
* dynamodb
* sns

## Pricing

Requests:
$0.20 per million requests after first (free) million

Duration:
Charged per millisecond. Rounded to 100ms. Charge stops when lambda terminates.

No servers. Continuous scaling (out, not up). Cheap.

1 event can trigger a chain of lambda functions or multiple lambda functions.

Lambda can be used globally. Can be used to backup S3, etc.

**AWS X-ray** can be used to debug complicated architectures.

Max execution duration of 5 min per function.


## Building a serverless webpage

API gateway and lambda

Use a role for the Lambda function to access other services.

API Gateway: enable CORS (cross origin content sharing) because domain name of api gateway is different to s3 domain name.
