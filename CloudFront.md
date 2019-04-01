# CloudFront (CDN)

* CDN: system of distributed servers that deliver content and webpages to a user based on location of user, webpage server and CDN server.
* Edge location: where content will be cached (separate to Availabilty Zone). 50+ ELs in the world.
* Origin: origin of files to be distributed. Can be S3, Ec2, ELB or route53. Can also work with any other (non-aws) web server.
* Distribution: name of the CDN consisting of several edge locations. Two types:
  - Web distribution
  - RTMP (flash, streaming)

Edge locations can be read from and written to.

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
* Origin: domain name, path (optional, for subfolders in origin), access identity, permissions
* Origin access identity
* TTL: important design consideration (how often are files updated?)
* Restrict viewer access: to restrict access to certain users (pre-signed URLs or cookies)
* SSL certs
* Geo restrictions: whitelist or blacklist (not both)
* Invalidations: for quick removal of sensitive items that have been accidentally cached

CloudFront has own URL, S3-url access can be restricted.
