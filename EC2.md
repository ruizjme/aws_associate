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

By default, EBS volumes are deleted on EC2-instance termination.

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
