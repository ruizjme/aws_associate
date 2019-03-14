# CloudFront (CDN)

* CDN: system of distributed servers that deliver content and webpages to a user based on location of user, webpage server and CDN server.
* Edge location: where content will be cached (separate to Availabilty Zone). 50+ ELs in the world.
* Origin: origin of files to be distributed. Can be S3, Ec2, ELB or route53. Can also work with any other (non-aws) web server.
* Distribution: name of the CDN consisting of several edge locations
  - Web distribution
  - RTMP (flash, streaming)

Requests are automatically routed to nearest edge location.
Files are retrieved from origin to edge location.
Files are cached for t = TTL (time to live). Next request is serviced faster if file available.
Cache can be cleared at a charge.

CloudFront can be used to deliver:
* Dynamic content
* Static content
* Streaming content
* Interactive content

## Distribution

Using content from S3 bucket in location far away.
* Origin: domain name, path (optional), access identity, permissions
