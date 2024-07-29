# Elastic Beanstalk

Fully managed environment for web applications.  Upload source code in zip file. Everything within EB is launched and managed by Elastic Beanstalk.

- Best practice is to keep RDS outside of EB.
- Can launch EC2 instances or Docker containers instead of the zip file.
- Java, .NET, PHP, Node.js, Python, Ruby, Go and Docker.
- Tomcat for Java.
- Apache or PHP & Python.
- nginx or Apache for Node.js.
- Passenger or Puma for Ruby.
- IIS for .NET.
- Java SE.
- Docker.
- Go.

## Versions

- Applicat->Version1, Version2, Version3 etc.
- Each version is a specific reference to a section of deployable code
- Application version will typically point to an S3 bucket containing the code. Versions reside within bucket.
- Versions reside with Environment (Dev can run Version 3, Production can run Version 2).

## Web Servers and Workers.

- Web servers are standard applications that listen for HTTP requests.
- Workers are specialist applications that have a background processing task that listens for messages on an SQS queue.
- Use workers for long running tasks.

Example:
```` User->port 80->EB [ Web server -> SQS queue <-polling- Worker ] -> RDS ````

## Updating EB - Deployment Policies.

- All at once - simultaneous. Removes EC2 instance. If fails, rollback is to redploy, more downtime.
- Rolling - One/Few at a time.
- Rolling with additional batch, one at a time, but add additional EC2 before taking one out. £
- Immutable (launch new instances in an ASG, swap traffic over). ££
- Blue/green. Create new Stage environment and use R53 weighted routing policy. Not a feature of EB as such.
