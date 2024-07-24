

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

## Step Functions synchronous execution
````
-----------> Time---------->
[Job1]->[Job2]->[Job3]->[Job4]
````

## Step Functions synchronous execution
````
-----------> Time---------->
[Job1]
[Job2]
[Job3]
[Job4]
````