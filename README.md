# Azure VM + Load Balancer Demo

## Overview
This project provisions two Azure Virtual Machines (VMs) behind an Azure Load Balancer to ensure high availability and traffic distribution.

## Tech Stack
- Azure Virtual Machines
- Azure Load Balancer
- Azure CLI
- IIS Web Server (for demo purposes)

## Architecture
A simple two-tier architecture:
- Frontend: Azure Load Balancer
- Backend: Two Azure VMs running IIS

## Steps
1. Create a resource group:
   ```bash
   az group create --name demo-rg --location eastus
   ```

2. Create two VMs:
   ```bash
   az vm create --resource-group demo-rg --name vm1 --image Win2019Datacenter --admin-username azureuser --admin-password YourPassword123!
   az vm create --resource-group demo-rg --name vm2 --image Win2019Datacenter --admin-username azureuser --admin-password YourPassword123!
   ```

3. Install IIS on both VMs (run inside each VM):
   ```powershell
   Install-WindowsFeature -name Web-Server -IncludeManagementTools
   ```

4. Create a Load Balancer and backend pool.

5. Add health probes and rules to forward HTTP traffic.

6. Associate VMs with the backend pool.

7. Test high availability by accessing the Load Balancer IP.

## Outcome
Users accessing the Load Balancer IP are routed to one of the two IIS servers, confirming proper traffic distribution and redundancy.

---
> Created as part of an Azure Cloud Engineering Portfolio.
