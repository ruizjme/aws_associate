# Well Architected Framework: Pillars

## Security

### Data protection
classify data in confidentiality levels. Least privilege access.
KMS, IAM, versioning. SSL, ELB, RDS, S3.

### Privilege management
ACL
Role based
Password managment

MFA, roles, groups, keys, credentials

### Infra protection
VPC, SGs, NACLs, separate subnets

### Detective controls
Cloudtrail, cloudwatch, s3, glacier, config

## Reliability

Test recovery procedures
Automatically recover from failure
Scale horizontally
Stop guessing capacity

### Foundations
service limits, topology, escalation path for tech issues
IAM, VPC

### Change management
Adapt to changes, monitor resources, how is change managment executed
Cloudtrail

### Failure managment
Back up data, component failures, plan for recovery
Cloudformation


## Performance efficiency

Design principles:

Democratise advanced technologies
Go global in minutes
Use serverless architectures

### Compute
Select appropriate instance type
Continue to use the most appropriate instance type when new features are introduced
Monitor instnances post launch
Match instances to demand

### Storage
Select appropriate solution
continue to have most appropriate solution when new features are introduced
Monitor
Match demand

### Database
Select appropriate solution
continue to have most appropriate solution when new features are introduced
Monitor
Match demand

### Space-time tradeoff
Proximity, caching
Select appropriate solution
continue to have most appropriate solution when new features are introduced
Monitor
Match demand


## Cost Optimisation

Transparently attribute expenditure
Managed services reduce cost of ownership
Trade capital expense for operating expense
Benefit from economies of scale
No spending on data center operations

### Matched supply and demand
Match needs without exceeding
Optimise use of AWS services

### Cost-effective resources
Resource type
pricing model
Can managed services be used (instead of ec2, ebs or s3) to improve ROI

### Expenditure awareness
ACLs to govern costs
Monitor usage and spending
Decommission resources, stop resources
Data transfer charges

### Optimising over time
Adoption of new services


## Operational Excellence
Perform operations with code
Align operations processes to business objectives
Make regular, small, incremental changes
Tests for responses to unexpected events
Learn from operational events and failures
Keep operations procedures current

### Preparation
### Operation
### Response
