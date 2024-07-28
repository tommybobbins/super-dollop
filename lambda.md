
## Lambda function invocations

### Synchronous

- e.g. CLI, SDK, API Gateway
- Result returned immediately
- Error processing happens client side (retries, exponential backoff)

### Asynchronous

- e.g. S3, SNS, Cloudwatch events
- Lambda retries up to 3 times
- Processing must be idempotent

### Event Source mapping

- SQS, Kinesis Data Streams, DDB streams.
- Lambda does the polling.
- Records are processed in order (except SQS standard).
- SQS can also trigger lambda *OR* lambda can poll SQS!

### Lambda function concurrency

- Additional functions are initialized up to the burst or account limit.
- If the concurrency limit is exceeded, throttling occurs with error "Rate exceeded" and 429,
"TooManyRequestsException"
- Burst concurrency is 3000, 1000, 500 depending on region.
- Check for throttling messages in Cloudwatch logs
- If there are no Lambda throttles metrics, the throttling is happening on the API calls
- For asynchronous lambda retries, after 3 times, will go to DLQ.
- DLQ can go to either SNS topic or SQS queue.

If you have throttling

- Configure reserved concurrency
- Exponential backoff
- Concurrency metrics

## Step Function Execution Guarantees

|Product | Standard Workflows|Express Workflows: Synchronous and Asynchronous|
| --- | --- | --- |
|Duration |One year	|Five minutes|
|Supported state transition rate| Limited| Unlimited|
|Pricing|Priced by number of state transitions. A state transition is counted each time a step in your execution is completed.|Priced by the number of executions you run, their duration, and memory consumption.|
|Execution history|Executions can be listed and described with Step Functions APIs. Executions can be visually debugged through the console. They can also be inspected in CloudWatch Logs by enabling logging on your state machine.| Unlimited execution history, that is, as many execution history entries are maintained as you can generate within a 5-minute period. Executions can be inspected in CloudWatch Logs or the Step Functions console by enabling logging on your state machine.|
|Execution semantics|Exactly-once workflow execution.| Asynchronous Express Workflows: At-least-once workflow execution.Synchronous Express Workflows: At-most-once workflow execution.|
|Service integrations|Supports all service integrations and patterns.|Supports all service integrations.
* Express Workflows do not support Job-run (.sync) or Callback (.waitForTaskToken) service integration patterns*.|
|Step Functions activities|	Supports Step Functions activities.|Doesn't support Step Functions activities.|


- *Asynchronous Express Workflows* return confirmation that the workflow was started, but don't wait for the workflow to complete. To get the result, you must poll the service's CloudWatch Logs. You can use Asynchronous Express Workflows when you don't require immediate response output, such as messaging services or data processing that other services don't depend on. You can start Asynchronous Express Workflows in response to an event, by a nested workflow in Step Functions, or by using the StartExecution API call.
- *Synchronous Express Workflows* start a workflow, wait until it completes, and then return the result. Used to orchestrate microservices. With Synchronous Express Workflows, you can develop applications without the need to develop additional code to handle errors, retries, or run parallel tasks. You can run Synchronous Express Workflows invoked from Amazon API Gateway, AWS Lambda, or by using the StartSyncExecution API call.


## Step Functions standard execution
````
-----------> Time---------->
[Job1]->[Job2]->[Job3]->[Job4]
````

## Step Functions express execution
````
-----------> Time---------->
[Job1]
[Job2]
[Job3]
[Job4]
````
## Step functions synchronous
````
[Job1]->[ACK]
````

## Step functions standard synchronous
````
-----------> Time---------->
[Job1]->Ack->[Job2]->Ack->[Job3]->Ack->[Job4]->Ack
````
## Step functions express synchronous
````
-----------> Time---------->
[Job1]->Ack
[Job2]->Ack
[Job3]->Ack
[Job4]->Ack
````


## Lambda Versions and Aliases

Updating lambda versions and pointing an application to those versions.

### Lambda versions
MyFunction:$LATEST -> Edit -> MyFunction:1

- Snapshot is saved to a new version MyFunction:1
- New version includes function code, dependencies, runtime, function settings and a unique ARN.
- Versions are immutable 1,2,3,4,.
- Because different versions have different ARNs this allows you to manage them for dev,uat,prd
- A qualified ARN has a version suffix ```` arn:aws:lambda:eu-west-2:1234568907:function:MyFunction:1 ````
- An unqualified ARN does not have a version suffix
- You cannot create an ALIAS from an unqualified ARN.

What is an Alias?

- MyFunction:1, MyFunction:2 are lambda versions.
- MyFunction:testalias is an alias which may point to MyFunction:2.
- MyFunction:testalias can bluegreen and point 20%, 80% to MyFunction:1, MyFunction:2 respectively.


## Serverless Architecture patterns

- Decouple with SQS even if you are using EC2, can use EC2->SQS->Lambda->RDS.
- Scale processing tier (ASG) based on SQS queue length.

TBC
