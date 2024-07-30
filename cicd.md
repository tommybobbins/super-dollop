# Deployment and Management

## CICD

````
Developer->Github/CodeCommit<-Codebuild-----------------------------> Deploy
                               Build servers build and test code
    <-----------------------------------------| Results
````

## Code Commit

- Fully managed source control service. Git based.
- Can use IAM as well as SSH keys to auth.

## Code Pipeline

- Continuous delivery system that automates release pipelines.
- Automates build, test and deploy phases everytime there is a code change based on the release model.
- Deploy stage: CloudFormation, Code Deploy, ECS, EB, AWS ServiceCatalog, S3.

### Pipeline

- A workflow that describes how software changes go through the release process.

### Artifacts

- Files or changes that will be worked on by the actions and stages in the pipeline.
- Each pipeline stage can create artifacts.
- Artifacts are passed, stored in S3 and then passed onto the next stage.

### Stages

- Pipelines are broken up into stages.
- Each stage can have sequential or parallel actions.
- Stage examples would be build, test, deploy, load test, etc.

## Code Pipeline with EB

````
           |--------CodePipeline------|
Developer->CodeCommit->ElasticBeanstalk----> EB Updates Application
````

buildspec.yml - Adds a build stage to a pipeline. Similar to bb pipeline steps / Github actions. Can also use a custom filename if required. Can change the container of the stage if required.


## CodeGuru

### CodeGuru Reviewer

- Can examine Java and Python and make suggestions for improvement using ML.
- Suggestions based on best practice.
- Can find resource leak and security problems
- Integrates with Secrets Manager to find unprotected secrets in code.
- Supports Code Commit, Bitbucket, Github, S3.

### CodeGuru Profiler

- Collects runtime performance data from your live applications.
- Helps fine-tune application performance.
- What code is running on the CPU
- Time consumed.
- Methods to reduce CPU.
- Reduce costs
- Performance insights
- Heap utilization over time.


## AWS CodeStar

- Quickly develop build and deploy applications on AWS.
- Preconfigured CD toolchain for building, testing and deploying.
- Use project templates to develop applications on EC2, Lambda, EB.
- Use code editors such as VS, Eclipse or the AWS CLI.

````
IDE->CodeStar integrates and orchestrates->[AWS Cloudformat + CodeCommit + CodeBuild + CodeDeploy]
````

## AWS Cloud 9

- Cloud based IDE
- Write, Run, Debug code with just a brower
- Integrated tools for JS, Python, PHP, Serverles development, SDKs libraries etc.
- Realtime collaboration between team members.

## AWS Code Artifact

- Stores artifacts using popular package managers - Maven, Gradle, npn, Yarn, Twine, pip and NuGet.
- Automatically fetches software repos on demand from public repos.
- Securely share private packages across organisations by publishing centrally.
- Build automated approval workflows using CodeArtifact APIs and Eventbridge.
- AWS Privatelink possible.