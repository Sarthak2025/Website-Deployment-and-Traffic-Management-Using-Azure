# Website-Deployment-and-Traffic-Management-Using-Azure

## Overview
Deploy a website across two Azure regions (Central US, West US) with traffic distribution using Traffic Manager. The site includes:
1. **Home Page** (VM2)
2. **Upload Page** (VM1, files uploaded to Azure Blob Storage)
3. **Error Pages** (403, 502 errors via Azure Storage static site)

## Components
- **VMs in VNets**: Deployed in both regions, connected via VNet Peering.
- **Application Gateway**: Routes traffic to correct pages, handles errors.
- **Blob Storage**: Hosts static `error.html`, stores uploaded files.
- **Traffic Manager**: Routes traffic between both regions' gateways.

## Setup Steps

### 1. Deploy VMs and VNets
- Create VM1 (Upload Page) and VM2 (Home Page) in each region.
- Peer VNets between regions.

### 2. Clone and Run Scripts
Clone the repo on both VMs:
```bash
git clone https://github.com/azcloudberg/azproject
Run setup scripts:

VM1 (Upload Page): ./vm1.sh
VM2 (Home Page): ./vm2.sh
3. Configure Blob Storage & Gateway
Blob Storage: Create a storage account, enable static site, upload error.html. Create an upload container for file uploads.
Application Gateway: Route example.com to VM2 (home) and example.com/upload to VM1 (upload). Set error handling to point to the error.html.
4. VM1 Configuration
Update config.py with your Storage Account details, then start the app:

bash
Copy code
sudo python3 app.py
5. Traffic Manager
Configure Traffic Manager to distribute traffic between both regions.

6. Verify
example.com for the home page.
example.com/upload to test uploads.
Test error handling for 403/502 errors.

This project is given by Intellipaat.
