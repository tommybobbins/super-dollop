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

## Migrate users from Active Directory to AWS Managed Microsoft AD

You can use the Active Directory Migration Toolkit (ADMT) along with the Password Export Service (PES) to migrate users from your self-managed Active Directory to your AWS Managed Microsoft AD directory. This enables you to migrate Active Directory objects and encrypted passwords for your users more easily.

https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_migrate_users.html

## Simple AD
Simple AD is a standalone managed directory that is powered by a Samba 4 Active Directory Compatible Server. It is available in two sizes.

- Small - Supports up to 500 users (approximately 2,000 objects including users, groups, and computers).

- Large - Supports up to 5,000 users (approximately 20,000 objects including users, groups, and computers).

Simple AD provides a subset of the features offered by AWS Managed Microsoft AD, including the ability to manage user accounts and group memberships, create and apply group policies, securely connect to Amazon EC2 instances, and provide Kerberos-based single sign-on (SSO). However, note that Simple AD does not support features such as multi-factor authentication (MFA), trust relationships with other domains, Active Directory Administrative Center, PowerShell support, Active Directory recycle bin, group managed service accounts, and schema extensions for POSIX and Microsoft applications.

https://docs.aws.amazon.com/directoryservice/latest/admin-guide/directory_simple_ad.html