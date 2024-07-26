# Autoscaling

## Autoscaling groups

Instance metrics are not counted until the warm-up time has expired.

## Dynamic scaling - target tracking

- ASGAverageCPUUtilization - Average CPU utilization of the ASG.
- ASGAverageNetworkIn - Mean bytes received on all network interfaces. 
- ASGAverageNetworkOut - Mean bytes sent out on all network interfaces.
- ALRrequestCountPerTarget - number of requests per target in an ALB.

### Target tracking with SQS

- ASG->SQS queue->AWS CLI/SDK->Cloudwatch->Launch instances to process backlog in SQS queue.

### Step scaling

- Size of alarm breach can determine the number of instances launched.

### Scheduled scaling

- 08:00 requires 8 instances, 11:00 back to normal. Recurrence and start time.
- Need a second scaling activity to return to normal

### Scaling processes

- Launch.
- Terminate.
- AddToLoadBalancer.
- AlarmNotification. (Accepts notifications from CW alarms)
- AZRebalance. (Balances the number of EC2s across all AZs)
- Healthcheck (collected from EC2 metrics and ELB).
- ReplaceUnhealthy. 
- ScheduledActions (scheduled scaling)

Cooldowns are used to prevent autoscaling from launching or terminating before effects of previous activities are visible.
Termination Policy - controls which instances to terminate first when a scale in event occurs.

### Lifecycle hook

When reducing the number of instances, lifecycle hook can pause the termination and allow a snapshot to take place.
Modify ASG so that Lifecycle hook->EC2_INSTANCE_TERMINATING-> SNS -> Lambda runs-> Snapshot
