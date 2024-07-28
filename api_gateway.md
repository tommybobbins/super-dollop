# API Gateway

## Inputs 

- Swagger
- Open API 3.0

## Outputs

- Lambda
- Any other AWS Service
- Lambda in a private subnet
- EC2 instance
- Application Load Balancer
- Any public Endpoint (outside or inside AWS)

## Deployment types

- *Edge-optimized endpoint* = Cloudfront + API Gateway = Reduced Latency for requests from around the world.
- *Regional endpoint*  = Services in same region + API Gateway = Reduced Latency for requests in the same region. Configure your own CDN and protect with WAF.
- *Private endpoint* = Services in the same VPC + API Gateway. Securely expose your REST APIs only to other services within the VPC or connect via DX.

## Integrations

- For a lambda function you can have lambda proxy integration or lambda custom integration.
- For an HTTP endpoint you can have HTTP proxy integration or HTTP custom integration.
- For an AWS service action you have the AWS integration of the non-proxy type only.

## Caching

- Can add caching to API calls by provisioning an API Gateway cache and specifying it's size in GB, Encryption and TTL.
- Caching allows you to cache the endpoints responses.
- Reduces the calls to the backend, improve latency.

## API throttling

- Steady state rate and burst of request submissions.
- 10K/s steady state request rate.
- 5K/s requests across all APIs within an AWS Account.
- If you exceed these limits you will receive a 429 TooManyRequests error response.
- Can build an application to defensively retry for this.

## API Gateway - Usage Plans and API keys

- Different Public Endpoints with API key for premium customers.
- Higher rates for throttling and burst for premium customers.
- Per method throttling limits.
