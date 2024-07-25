# Identity Providers and Federation

## IAM - SAML 2.0 Identity Federation

````
Users->[ AD ] --> ADFS --> IdP sends client SAML assertion --> App --> AWS STS (sts:AssumeRoleWithSAML) returns temp creds:
                                                                <----------------|
                                                                --------------------------------------------> DDB
````


## IAM - Web Identity Federation

- Amazon
- Google
- Facebook
- Mobile App
- Any OIDC compatible supported application

````
Users->[ Social IDP ] --> App --> AWS STS (sts:AssumeRoleWithWebIdentity) returns temp creds:
                          <----------------|
                          --------------------------------------------> DDB
````

AWS Recommend using Cognito for web identity federation in most cases.

## IAM - Identity Center

Is the successor to AWS SSO. Identity sources can be Identity Center directory, Active directory and standard providers using SAML 2.0. It enables centralized permissions management and SSO.

- AD (self-managed) / Azure AD 

````
Users->[ AD ] --> AD Connector or AWS Managed Microsoft AD --> IAM Identity Centre --> Pre-configured Applications (Office 365/Slack etc)/Custom SAML 2.0 application. 
````
Can also integrate with AWS Organizations and underlying accounts.

### Cognito

````
Users --> App --> Cognito User Pool --> Cognito IdP --> AWS STS (sts:AssumeRoleWithWebIdentity) returns temp creds:
          Social IDp <----->                     
           --------------------------------------------------------------> DDB
````
