# Azure ARM VM Deployment

## Overview
Deployed Ubuntu Linux VM using ARM Template
via Azure CLI on Azure Cloud Shell as part
of Cloud Computing Bootcamp.

## Resources Deployed
| Resource | Name |
|---|---|
| Virtual Machine | myUbuntuVM |
| Public IP | 102.37.110.34 |
| Virtual Network | myVNet |
| Subnet | mySubnet |
| NSG | myNSG |
| NIC | myNIC |
| Location | South Africa North |
| VM Size | Standard_D2s_v3 |
| OS | Ubuntu 20.04 LTS |

## Deployment Outputs
- **Public IP:** 102.37.110.34
- **SSH Command:** ssh azureuser@102.37.110.34
- **Private IP:** 10.0.0.4
- **Created:** 6/14/2026 6:30 PM UTC## CLI Commands Used

### Validate Template
```bash
az deployment group validate \
  --resource-group Cloud-bootcamp \
  --template-file template.json \
  --parameters parameters.json
### Deploy Template
```bash
az deployment group create \
  --resource-group Cloud-bootcamp \
  --template-file template.json \
  --parameters parameters.json
az vm show \
  --resource-group Cloud-bootcamp \
  --name myUbuntuVM \
  --show-details \
  --output table
## ARM Template Structure
| Section | Purpose |
|---|---|
| parameters | VM name, size, credentials, location |
| variables | Network resource names |
| resources | NSG, VNet, Public IP, NIC, VM |
| outputs | Public IP and SSH command |

## Troubleshooting
| Error | Solution |
|---|---|
| B1s SKU unavailable | Used Standard_D2s_v3 |
| Basic IP quota exceeded | Changed to Standard SKU Static IP |

## Completion Checklist
- [x] ARM template created
- [x] Networking configured
- [x] VM deployed via CLI
- [x] VM verified running
- [x] Output log captured
