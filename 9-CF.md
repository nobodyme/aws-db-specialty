## Some points that I forget
-  CloudFormation Stack Policies can be used to deny actions on specific stack or resources to protect them from unintended modifications.
-  B. Implement CloudFormation Stack Policy: { "Effect" : "Deny", "Action" : "Update:*", "Principal": "*", "Resource" : "LogicalResourceId/ProductionDatabase" }