# SQS

Amazon Simple Queue Service (SQS) is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications. SQS offers two types of message queues - Standard queues vs FIFO queues.

By default, FIFO queues support up to 300 messages (API calls) per second (300 send, receive, or delete operations per second). When you batch 10 messages per operation (maximum), FIFO queues can support up to 3,000 (300*10) messages per second.


## Message timers
You can use message timers to set an initial invisibility period for a message added to a queue. So, if you send a message with a 60-second timer, the message isn't visible to consumers for its first 60 seconds in the queue. The default (minimum) delay for a message is 0 seconds. The maximum is 15 minutes. Therefore, you should use message timers to postpone the delivery of certain messages to the queue by one minute

## SQS Queue Types

| Standard Queue | FIFO Queue |
| --- | --- | 
| Unlimited throughput | High Throughput 300 op/s, 3000 op/s with batching|
| Best-Effort ordering|First in, first out|
| At-least once delivery|Exactly once processing|

## SQS DLQ

Message not processed successfully - ReceiveCount exceeds maxReceiveCount for queue. Message goes to the DLQ
Analyze the DLQ for failures

Main task of the DLQ is handling message failures. A DLQ lets you set aside and isolate messages that can't be processed correctly to determine why their processing failed.
It's not a queue type, it is a standard or FIFO queue that has been specified as a DLQ in the configuration of another standard or FIFO queue.
When you configure SQS need to provide the following config for the DLQ:

- Redrive policy: boolean
- DLQ name: string
- Maximum receives: integer # Maximum receives before a message is sent to the DLQ


## SQS Delay Queue 

Specify a delay in seconds before a message is visible. Configurable 30 seconds - 15 minutes

## SQS Long Polling vs Short Polling

- LongPolling prevents consumer from tight looping on the CPU. WaitTimeSeconds before announcing queue is empty.
- ShortPolling returns immediately that the queue is empty. 

