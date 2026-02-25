```mermaid
flowchart LR
    RemotePC[Remote PC]
    STHub[ST Hub Cloud]
    AWSspoke[AWS Spoke]
    Server[Server in AWS]
    BranchPCs[Branch PCs]
    BranchSpoke[Branch Spoke]

    RemotePC --> STHub
    STHub --> AWSspoke
    AWSspoke --> Server
    BranchPCs --> BranchSpoke
    BranchSpoke --> STHub
```
