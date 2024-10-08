# AWS App Sync

Is a managed service using GraphQL or Pub/Sub APIs which makes it easy for Applications to get the data they need from NoSQL datastores, RDBMS, HTTP APIs and lambda.

- Can retrieve data in real time with Websocket or MQTT on Websocket.
- Commonly used for Mobile Applications, IoT, Offline/intermittent apps: local data access + Data sync.
- It is stood up with uploading a GraphQL schema.

## Integrates with

- DynamoDB
- Aurora
- Opensearch
- Lambda
- HTTP -> Public HTTP APIs
- Cloudwatch Metrics and Logs.

## Cognito Authorisation

- Perform Auth on Cognito users based on groups they belong to.
- In the GraphQL schema, you specify the security for those Cognito groups.
- ```` @aws_auth/cognito_groups: (["bloggers","readers"])````
- Authorization via Cognito JWT.
