# CloudFront

- Content is pushed from the origin and cached.
- Edge locations are distributed around the world.

## CloudFront Distribution
- ````d213212123124sdfss.cloudfront.net```` 
- S3 Origin.
- CloudFront Web Distribution. 
- Custom Origin.
- Live Streaming (RTMP distributions went away).
- 12 Regional Edge Cache sits between Origin and Edge Locations.
- 210 Edge locations<->Users.
- Files are cached at the edge locations.
- CloudFront Path Patterns, pick a different origin based on host header path

You can configure Cloudfront to forward headers in the viewer request to the origin:
- Cloudfront can then cache multiple versions of an object based on the values in one or more request headers
Controlled in a behaviour to do one of the following:
- Forward all headers to your origin (objects are not cached).
- Forward a whitelist of headers that you specify.
- Forward only the default headers (doesn't cache objects based on values in request values).

### Behaviours

- Path Pattern
- Viewer Protocol Policy
- Cache Policy
- Origin Request Policy

### CloudFront Signed URLs and OAI/OAC

Signed URLs provide more control over access to your content:
- Beginning and expiration date / time.
- IP addresses allowed to access.

### Signed Cookies

- Similar to Signed URLs.
- Use Signed Cookies when you don't want to change URLs.
- Can also be used when you want to provide access to multiple restricted files (Signed URLs for one file only).

### OAI

Origin Access Identifier- Use OAC instead.

- Bucket policy only allows the CloudFronts OAI to access the bucket.

### OAC

Origin Access Control replaces the OAI but supports additional use cases.

- Bucket policy, but the Principal is the service and the Resource is the CF Distribution.

### Cloudfront ACM

- Certificate can be ACM or a trusted third-party CA.
- Certificate must be located in us-east-1.
- Default CF domain name can be changed using CNAMES
- Custom Origin - Certificate can be ALB or 3rd Party
- Origin certificates must be public certificates.

Viewer protocol works out how to deal with HTTP and HTTPS
SNI - multiple certificates for a single origin can exist if you need to route to S3 / Custom Origin

### Lambda@Edge

- Run Node.js and Python Lambda functions to customize the content cloudfront delivers.
- Execute functions close to the viewer.

Can be run at the following points:

- After CF receives a request from a viewer (viewer request).
- Before CF forwards the request to the origin (origin request).
- After CF receives the response from the origin (origin response).
- Before CF forwards the request request to the viewer (viewer response).

### AWS Global Accelerator

Networking service to use AWS Global application to use AWS Network for data transfer, consistency.
Provides a static *anycast* IP to connect to endpoints (useful for allowlists). Will still be directed towards your closest edge location.
Traffic traverses the AWS global network.
Similar to cloudfront, can perform failover.
