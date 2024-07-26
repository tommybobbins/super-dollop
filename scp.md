# SCP

- SCPs do not affect service-linked role
- SCPs affect all users and roles in attached accounts, including the root user
- If a user or role has an IAM permission policy that grants access to an action that is either not allowed or explicitly denied by the applicable SCPs, the user or role can't perform that action