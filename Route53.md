# Route53

The Route53 operates globally. (no region in console)

# DNS

Top level domains controlled by IANA iana.org/domains/root/db

**Domain registrars** (e.g. GoDaddy, AWS) Authorities that can assign domain names directly under top-level domains. Domain names are registered under InterNIC, in a central DB (WhoIS)

## Time to live
In seconds, length that a DNS record is cached in resolver server.

# SOA records
Start of authority

## Name server records
web address, TTL, nameserver

## A record
A for address
translates domain name to IP address.

## MX records
email server records

## CNAMES

Canonical names: maps one domain name to another (e.g. m.example.com to mobile.example.com)

## Alias records
Unique to Route53. Like cnames, except it allows mapping naked domain names.

Given the choice, alias record is preferred (in AWS).

### Notes
ELBs don't have IP addresses. Use DNS name.


# Routing policies

* Simple
* Weighted
* Latency
* Failover
* Geolocation

They can't be mixed for a given domain (with some exceptions).

## Simple routing

e.g. one web server serving a website or one ELB for one website.

## Weighted routing

Allows for splitting traffic based on weights assigned to targets.

## Latency based routing

Allows to route traffic for lowest latency for end user (fastest response time).
Specify records for each location of web server. The service will choose where to route the traffic for lowest latency

## Failover routing
To create a active/passive set up.

Create a health check for domain name or IP address in the Route53 console.

Associate the failover routing policy to the health check. One policy for the primary and another one for the secondary (both associated to the same health check).

## Geolocation routing

Send users to one web server or another based on their location.

## Multivalue answers

Multiple servers with health checks. Servers are removed from list if health check is failed. (Think kind of like a LB that can work across regions (LBs can't).)
