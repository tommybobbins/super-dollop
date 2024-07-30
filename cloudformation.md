# CloudFormation

Infrastructure patterns are defined in a template file using code (json or yaml). Cloudformation builds infrastructure according to the template.

- Infrastructure provisioned consistently.
- Fewer mistakes, human error.
- Reusable templates (define once, keep re-using).
- Pay for the resources provisioned.
- Allows rollback once complete.

|Component|Description|
|---|---|
|Templates|JSON or YAML text described by the template and created, updated and deleted as a single unit.|
|Stacks|The entire environment described by the template and created, updated and deleted as a single unit|
|StackSets|AWS CloudFormation Stacksets extends the functionality of stacks by enabling you to create, update and delete stacks across multiple accounts and regions within a single operation.|
|Change Sets|A summary of proposed changes. Preview mode.|