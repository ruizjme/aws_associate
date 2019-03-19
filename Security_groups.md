

# Security Groups

vritual firewall

One EC2 instance is associated to one or more Security Groups

inbound rules
all inbound traffic is blocked by default

outbound rules
all outbound traffic is allowed by default

rule changes apply immediately

rules are **stateful**: outbound rules are implicit based on inbound rules (doesn't matter if an outbound rule is deleted if there is an equiv inbound rule)

traffic cannot be denied with security groups, only allowed.
one cannot block specific IP address using SGs (should use network ACLs)

To apply SG to instances: Actions > networking > Security Groups


# EBS volumes
