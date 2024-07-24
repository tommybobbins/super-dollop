

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