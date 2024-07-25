# Directory Services and Federation

Can have a one way or two way trust relationship with Microsoft AD (Windows EC2 instances able to be logged into using credentials from the corporate AD). AWS Managed Microsoft AD.

## ADSync 

Synchronisation to AzureAD /Office365

## ADFS

Federation to AzureAD/Office365.

## Apps that support MS authentication and authorization using AWS Directory Services

- Console
- Workspaces
- RDS
- Workdocs
- QuickSight
- Workmail

It also allows you to:

- Apply Group Policy.
- Use SSO with Apps and Services.
- Enable MFA with RADIUS.


# AD Connector

Self managed AD in corp office. Want these accounts to access AWS.

````
[ AD ] --> VPN --> [ AD Connector --> Amazon Workspaces ]
                    [            --> AWS Management Console (Provides federated sign-in by mapping AD identities to IAM Roles)]
                    [           <-> Windows EC2 (bidection, can join on prem domain) ]
````