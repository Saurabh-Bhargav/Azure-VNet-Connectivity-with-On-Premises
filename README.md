# Building Secure Interconnected Networks: A Hands-On Azure Lab Experience

## Project Overview
The "Building Secure Interconnected Networks" project provides a comprehensive hands-on experience in Azure, focusing on creating and securing interconnected virtual networks. This lab aims to demonstrate how to establish secure communication channels between Azure virtual networks and on-premises environments using various Azure networking features.

## Project Details

### Network Diagram

![Screenshot 2023-11-08 152254](https://github.com/Saurabh-Bhargav/Azure-VNet-Connectivity-with-On-Premises/blob/main/Images/NetworkDaigram.png)



### Lab Environment Setup
In this lab, we set up the following Azure resources:

- **Virtual Networks**:
  - **HUB-vnet1**: Azure virtual network serving as the central hub.
  - **SPK-vnet1**: Azure virtual network representing a satellite location.

- **Virtual Machines**:
  - **HUB-VM1**: Windows Server 2022 VM in the HUB-vnet1.
  - **SPK-VM1**: Windows Server 2022 VM in the SPK-vnet1.
  - **On-Premises VM**: Windows Server 2019 VM located in an on-premises environment with IP 192.168.10.10.

### Networking Configuration
- **Subnets**:
  - **HUB-vnet1**:
    - Subnet1: 10.100.0.0/24
    - GatewaySubnet: 10.100.1.0/24
    - AzureFirewallSubnet: 10.100.2.0/24

  - **SPK-vnet1**:
    - SPK-prvt: 10.200.0.0/24

- **Gateway**:
  - Created a Virtual Network Gateway (VNG1) in HUB-vnet1 for connecting to the on-premises network. Assigned a public IP for this gateway.

- **Local Network Gateway (LNG)**:
  - Configured LNG with the on-premises public IP and private IP for establishing a connection to VNG1.

### Networking Setup Steps
1. Created VNG1 in HUB-vnet1, utilizing the GatewaySubnet.
2. Configured LNG with on-premises IP details.
3. Established a connection between VNG1 and LNG using IKEv2 authentication.

### Network Peering
- Established peering between HUB-vnet1 and SPK-vnet1.
- Allowed SPK-vnet1 to use the gateway from HUB-vnet1.
- Allowed HUB-vnet1 to access the gateway from the SPK-vnet1.

### Remote Access Configuration
- Configured the on-premises VM for remote access.
- Updated routing and remote access options with VNG1's public IP and Azure IP range.
- Set up IKEv2 authentication for the VPN connection.

### Firewall Setup
- Created Azure Firewall in the AzureFirewallSubnet of HUB-vnet1.
- Configured firewall rules:
  - Blocked internet access for SPK-vnet1.
  - Allowed internet access for HUB-VM1.
  - Allowed both HUB-vnet1 and SPK-vnet1 to access the on-premises machine.

### Routing Tables
- Created route tables for HUB, SPK, and on-premises networks.
- Directed traffic from subnets to Azure Firewall for inspection.

### Testing and Validation
- Tested connections between on-premises, SPK, and HUB networks.
- Utilized `tracert` command to verify traffic flow through the firewall.
- Confirmed RDP and ICMP working bidirectionally for all machines.

## Conclusion
The "Building Secure Interconnected Networks" lab provided a practical understanding of Azure networking capabilities. By setting up virtual networks, gateways, peering, and firewalls, we ensured secure and efficient communication channels between Azure resources and on-premises environments. Through hands-on configuration and testing, participants gained valuable insights into creating robust and secure network architectures in Azure.

For detailed instructions and step-by-step guides, refer to the full documentation and code snippets in the project repository.


