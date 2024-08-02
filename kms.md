# KMS

- Create and Manage symmetrics and asymmetrics encryption keys
- KMS keys are protected by AWS HSM (not always customer HSM).
- Customer Managed Keys
- AWS Managed Keys (e.g. aws/ebs). Cannot manage, rotate or change them.
- Developer created keys are CMK.
- KMS by default creates the key material for a KMS key, can import yourself if required.
- KMS key can encrypt data up to 4KB.
- KMS key can generate, encrypt and decrypt Data Encryption keys (DEKs) if you need to encrypt large amounts of data.

# Alternative Key Stores

## External Key Store 

- Keys can be stored outside of AWS to meet regulatory requirements.
- You can create a KMS key in an external Key Store (XKS).
- All keys are generated and stored in an external key manager.
- When using an XKS, key material never leaves your HSM.

## Custom Key Store

- You can create KMS keys in an AWS CloudHSM custom key store.
- All keys are generated and stored in a CloudHSM cluster that you own and manage.
- Crypto operations are performed only in the CloudHSM cluster. 
- Custom key stores are not available for asymmetric KMS keys.

## Data Encrpytion Keys

 - Large amounts of data.
 - KMS keys generate, encrypt and decrypt data keys.
 - KMS does not store, manage or track your data keys or perform crypto with data keys.
 - Use and Manage Data keys outside of KMS.


 ## KMS Key rotation

 |Type of KMS Key|Customer Managed|AWS Managed|AWS Owned|
 |---|---|---|---|
 |Can View|Yes|Yes|No|
 |Can Manage|Yes|No|No|
 |Used only for my account|Yes|Yes|No|
 |Automatic rotation|Optional. Every 365 Days|Required. Every 365 days|Varies|

 - Cannot Enable or Disable Key rotation for AWS owned keys
 - Automatic key rotation is supported only on symmetric encryption KMS keys with Key material that AWS KMS generates (Origin = AWS_KMS).
 - Rotation changes the key material not the Key ID, ARN, region, policies or permissions.
 - After you enable key rotation, KMS rotates the KMS key automatically every year.
 - Automatic rotation is not supported for Asymmetric KMS keys, HMAC KMS keys, KMS keys in custom key stores.  
 - Can do manual key rotation, which changes the key_id. You can use an Alias to refer to the key.

 ## KMS Key Policies

- Need to allow the correct KMS actions to allow a user to use a key
- Multiple policy statements can be combined to specify user and admin permissions.
- Grants are useful for temporary permissions as they can be used without modifying key policies or IAM policies. 

## Exam Tips

- To share snapshots with another account, you must specify ````Decrypt```` and ````CreateGrant```` permissions.
- The kms:ViaService condition key can be used to limit key usage to specific AWS services (EC2, RDS).
- Cryptographic erasure means removing the ability to decrypt data and can be achieved when using imported key material and deleting it. 
- You must use DeleteImportedKeyMaterial API to remove the key material.
- InvalidKeyId exception when using SSM Parameter Store means the KMS key is not enabled.

