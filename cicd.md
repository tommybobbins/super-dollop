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