# Day 2 â€“ Networking Core

## Objectives

- Learn VNet and subnet basics
- Understand NSGs, IP addressing, and DNS
- Build and test basic connectivity

## Key Concepts

- VNet = private network boundary in Azure
- Subnet = segmented network inside a VNet
- NSG = inbound/outbound traffic rules
- Public IP vs Private IP
- Azure-provided DNS vs custom DNS

## Hands-On Lab

1. Create a VNet
2. Create two subnets
3. Deploy a VM
4. Associate an NSG
5. Test allowed and denied traffic

## Exam Traps

- NSG rules use priority
- Lower number = higher priority
- NSGs can apply at subnet or NIC level
- A subnet is not the same thing as a VNet