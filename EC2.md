# EC2
Elastic Cloud Compute

Web service
Provides resizable compute in the cloud (virtual server)

## Pricing options

* **On demand**: pay fixed rate by hour or second with no commitment. Low cost, flexible with no upfront payment or long-term commitment. Applications with short term, spiky or unpredictable workloads that cannot be interrupted. Applications tested on EC2 for the first time.

* **Reserved**: capacity reservation. Discount on hourly rate. 1 or 3 year terms. Steady state or predictable usage. Up-front costs.

  - **Standard RI**: up to 75% off
  - **Convertible RI**: up to 45% off, can change attributes of instances as long as value of end instance >= initial value.
  - **Scheduled RI**: Available within reserved time window. Allows to match capacity reservation to predictable schedule.

* **Spot pricing**: bid desired price for instance capacity. Greater savings if application has flexible start/end times. Huge amounts of computing at odd times e.g. 4 am. Instance will be terminated if spot price goes above bid price. If terminated by price, no charge for partial hour. If terminated by user, there is charge for partial hour.

* **Dedicated hosts**: physical EC2 server dedicated for your use. Can help reduce costs by allowing use of server-bound software licences. Useful if regulatory requirements or licensing that prohibit multi-tenant virtualisation. Can be purchased on demand hourly. Also as a reservation at 70% off on-demand price

## Instance types

Mnemonic: FIGHT DR MC.PX

![](assets/EC2-a51a45f7.png)

## AMI

Template that contains software configuration (OS, App server, apps)

## Security group

Virtual firewall to allow access to instance through different ports (SSH, HTTP, etc)

## Key pair

SSH key pair used to SSH into instance.

## Volume encryption

Add volume and encrypt.
Root volume can only be encrypted if EC2 is copy of AMI with encrypted root.
Root volume cannot be encrypted for default AMIs (e.g. Amazon linux AMI).
Can be encrypted with 3rd party tools e.g. BitLocker.

## Monitoring

Every 5 min by default. Can be every 1 min at extra cost.
Uses CloudWatch.

## Termination protection
Off by default.

--------------------------------------------

# EBS

Virtual disk.
Can be attached to EC2, to create filesystem, install DB, etc.
Root device volume contains instance OS. Other volumes can be attached to EC2 instance.

By default, EBS root volumes are deleted on EC2-instance termination. Other volumes that may be attached to instance remain "available".

Volumes mounted to EC2 instance must be in the **same AZ**.

Volumes can now be modified (size and storage type) on the go with no downtime to EC2 instance.

EBS root volumes can now be encrypted via aws cli or console.

## Types
* General purpose SSD (GP2)
  - Balances price/performance
  - 3 IOPS per Gb with up to 10000 IOPS, ability to burst up to 3000 IOPS for extended periods for volumes at 3334 GiB and above.
* Provisoned IOPS SSD (IO1)
  - For IO-intensive applications (e.g. large relational NoSQL dbs)
  - Should be used if more than 10000 IOPS required.
  - Up to 20000 IOPS per volume
* Throughput optimised HDD (ST1)
  - Big data, warehouses, log processing
  - Cannot be boot volume
* Cold HDD (SC1)
  - Lowest cost, for infreq accessed
  - File server
  - Cannot be boot volume
* Magnetic (Standard)
  - Legacy
  - Lowest cost per Gb for bootable disk


## Snapshots

Snapshots are point in time copies of Volumes. Snapshots are incremental.

To migrate volume to another AZ, take snapshot, then copy to AZ, then create a new volume from the snapshot.

A new image can be created from a snapshot, which can then be booted as EC2 instance. Images appear under Images > AMIs. AMIs can be migrated to other AZs as well.

Snapshots exist on S3 (but are listed under EC2 in the console).

Snapshots can be encrypted when copying them. To have a root volume in an EC2 instance be encrypted, follow this procedure.

Snapshots of encrypted volumes are encrypted automatically.
Volumes from encrypted snapshots are encrypted automatically.
Snapshots can be shared only if unencrypted.

Best practice is to stop instance when taking snapshot.

## AMI Types

(Root device) EBS vs IS

Criteria:

* Region
* OS
* Architecture
* Launch permissions
* Storage: EBS or Instance Storage (ephemeral)

Instance store: cannot stop the instance, only terminate. The root device is created from a template stored in S3.


## Elastic Load Balancers


### Types
#### Application load balancers
For HTTP/HTTPS traffic. Operate at Layer 7 (application) are application aware. Intelligent request routing.

#### Network load balancers
Really fast, extreme performance. Operate at Layer 4 (connection). Millions of requests per second.

#### Classic load balancers
Old tech. ELB usually refers to CLB. HTTP/HTTPS. Can use Layer 7-specific features (e.g. x-forwarded, sticky sessions). Usually on Layer 4 relying on TCP only.

If app stops responding, CLB responds with 504 (means CLB is up but app or db server failed). Gateway timeout.

**X-Forwarded-For Header** can pass public IP address to app server.


### Health check
Load balancer performs regular health checks. If a target instance is unhealthy, no traffic will be directed to it. Instances can be InService or OutofService based on health checks.

LBs have a DNS name. You are not given an IP address.


## Auto Scaling groups

Create auto scaling group
Create launch configuration
Instances are evenly distributed across specified zones within region.

Deleting autoscaling groups deletes the instances.

# Placement groups

Clustered placement groups: within single AZ. Low latency and high network throughput.

Spread placement group: group of instances (opposite of clustered) ensures instances are in different hardware in different AZs.

Only some instances types can be launched in placement groups.

Should be homogenous in instance type

Can't be merged

Can't move existing instance into group.



# EFS

Elastic File System for EC2 instances. Storage capacity is elastic. EFS can be mounted to several instances.

Unlike EBS: 30c per Gb. Can scale up to Pb. Supports thousands of concurrent NFS connections.

Data is stored across multiple AZ's in region.

Read after write consistency.

Block storage.

Launching: Select AZs within region, vpc, subnet, IP address, sec group, tags.

EC2 instances that use EFS must be in the same VPC Security Group as the EFS volume.

Use case: file server across multiple EC2 instances. File and dir permissions apply.
