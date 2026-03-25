# Storage Security (HIGH VALUE)

## Access Priority

1. Azure AD (BEST)
2. SAS
3. Keys (AVOID)

---

## Network Security

| Feature | Purpose |
|--------|--------|
| Firewall | Restrict IP |
| Service Endpoint | Secure VNet access |
| Private Endpoint | Private IP |

---

## Data Protection

- Soft Delete = recover deleted blobs
- Versioning = restore previous versions
- Immutability = cannot modify/delete

# VM ADVANCED

## VM Extensions

- Custom Script Extension → run scripts
- Azure Monitor Agent → logging

---

## Disk Encryption

- Azure Disk Encryption (ADE)
- Uses Key Vault

---

## Run Command

- Execute commands without SSH/RDP

---

## Availability

- Set = same DC
- Zone = different DC

# NETWORK ADVANCED

## Azure Firewall vs NSG

| NSG | Firewall |
|-----|---------|
| Basic filtering | Advanced filtering |
| No logging | Full logging |
| No NAT | NAT support |

---

## Bastion

- Secure RDP/SSH via browser
- No public IP needed

---

## Load Balancing

| Service | Use |
|--------|-----|
| Load Balancer | Layer 4 |
| App Gateway | Layer 7 (HTTP) |

---

## Connectivity

| Type | Use |
|------|-----|
| VPN | Internet |
| ExpressRoute | Private connection |


# MONITORING ADVANCED

## Logs

| Type | Description |
|------|------------|
| Activity Log | Subscription level |
| Resource Logs | Resource level |

---

## Diagnostic Settings

👉 REQUIRED to send logs to Log Analytics

---

## Application Insights

- App performance monitoring

---

## KQL Example

DeviceProcessEvents
| where ProcessCommandLine contains "powershell"


# BACKUP & DR

## Azure Backup

- File/VM backup
- Uses Recovery Services Vault

---

## Azure Site Recovery (ASR)

- Full VM failover

---

## Concepts

| Term | Meaning |
|------|--------|
| RPO | Data loss |
| RTO | Downtime |

