# Cognito

## Cognito User Pools

- User Pool is a directory for managing sign-in ad sign-up for mobile applications
- Client/Mobile 

````
Users --> App --> Cognito User Pool --> Cognito IdP --> AWS STS (sts:AssumeRoleWithWebIdentity) returns temp creds:
          Social IDp <----->                     
           --------------------------------------------------------------> DDB
````

- Cognito User pool associated with Authentication (who am I?)
- Cognito acts as and Identity Broker between the IdP and AWS.
- Mapping between Users in AWS and an internal/external identity.

## Cognito Identity Pool

Used to obtain temporary, limited privilege credentials for AWS services. Authorization. The source can be a cognito user pool or it could be a facebook/apple/amazon/twitter identity provider. JWT.

It uses AWS STS to obtain the credentials, can then assume the role providing access to the AWS services.