# Azure Networking Flow

Internet  
â†“  
Public IP  
â†“  
Load Balancer or Application Gateway  
â†“  
Subnet  
â†“  
VM or App

## Core Controls

- NSG = traffic filter
- UDR = route override
- Azure DNS = name resolution
- Peering = private connection between VNets

## Exam Notes

- NSG rules are processed by priority.
- Peering is not transitive.
- UDRs can override system routes.