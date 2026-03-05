### ST Hub + Hub in AWS + Spoke + BWAN Clients
Good: No attack surface and remote user can connect to SD WAN.  
Bad: High cost
```mermaid
flowchart LR
    RemotePC[Remote PC]
    STHub[ST Hub Cloud]
    AWSHub[AWS Hub]
    Server[Server in AWS]
    BranchPC1[Branch PC1]
    BranchPC2[Branch PC2]
    BranchSpoke1[Branch Spoke1]
    BranchSpoke2[Branch Spoke2]

    RemotePC <--> STHub
    STHub <--> AWSHub
    AWSHub <--> Server
    BranchPC1 <--> BranchSpoke1
    BranchPC2 <--> BranchSpoke2
    BranchSpoke1 <--> AWSHub
    BranchSpoke2 --> AWSHub
```
### Hub in AWS + Spoke + BWAN Client
Good: low cost and remote users can connec to SD WAN.  
Bad: Attack surface
```mermaid
flowchart LR
    RemotePC[Remote PC]
    AWSHub[AWS Hub]
    Server[Server in AWS]
    BranchPC1[Branch PC1]
    BranchPC2[Branch PC2]
    BranchSpoke1[Branch Spoke1]
    BranchSpoke2[Branch Spoke2]

    RemotePC <--> AWSHub
    AWSHub <--> Server
    BranchPC1 <--> BranchSpoke1
    BranchPC2 <--> BranchSpoke2
    BranchSpoke1 <--> AWSHub
    BranchSpoke2 <--> AWSHub
```
### Hub in AWS + Spoke only
Good: no attack surface and low cost.  
Bad: remote user cannot connect to SDWAN Tunnel
```mermaid
flowchart LR
    AWSHub[AWS Hub]
    Server[Server in AWS]
    BranchPC1[Branch PC1]
    BranchPC2[Branch PC2]
    BranchSpoke1[Branch Spoke1]
    BranchSpoke2[Branch Spoke2]

    AWSHub <--> Server
    BranchPC1 <--> BranchSpoke1
    BranchPC2 <--> BranchSpoke2
    BranchSpoke1 <--> AWSHub
    BranchSpoke2 <--> AWSHub
```


