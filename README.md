# cisco-packet-tracer-subnetting
A 2-subnet network architecture designed in Cisco Packet Tracer separating Accounts and Delivery departments.
# Cisco Packet Tracer Network Design: Accounts & Delivery Department

A network design project implemented in Cisco Packet Tracer to establish secure and efficient connectivity between the **Accounts** and **Delivery** departments of an organization.

## 📌 Project Overview
The objective is to connect two distinct organizational departments using a single base network address, optimizing IP allocation via subnetting.

* **Base Network Address:** 192.168.40.0
* **Required Subnets:** 2 (Accounts Department & Delivery Department)
* **Hosts per Department:** Minimum 2 PCs each

## 📐 Subnetting Architecture
To split the base network into two functional subnets, a Custom Subnet Mask (FLSM) was calculated by borrowing 1 host bit as a network bit ($2^1 = 2$ subnets).

* **Subnet Mask:** 255.255.255.128 (Binary: `11111111.11111111.11111111.10000000`)

### Subnet Allocation Table

| Department | Network ID | Usable Host IP Range | Broadcast IP | Subnet Mask |
| :--- | :--- | :--- | :--- | :--- |
| **Accounts** | 192.168.40.0 | 192.168.40.1 – 192.168.40.126 | 192.168.40.127 | 255.255.255.128 |
| **Delivery** | 192.168.40.128 | 192.168.40.129 – 192.168.40.254 | 192.168.40.255 | 255.255.255.128 |

## 🛠️ Network Topology & Components
* **End Devices:** 4 PCs (2 assigned per department configured with respective static IPs, masks, and default gateways).
* **Intermediary Devices:** Cisco Switches (for departmental LAN segmentation) and a Cisco Router (to enable inter-VLAN / inter-subnet routing).
* **Cabling:** Appropriate Straight-Through cables for end-to-switch/switch-to-router connections.

## 🖼️ Topology Diagram
![Network Topology](topology.png)

## 🚀 How to Test & Verify
1. Download the `.pkt` file from this repository.
2. Open it in **Cisco Packet Tracer**.
3. Access the Desktop CLI of any PC in the **Delivery** department.
4. Run the ping command targeting an **Accounts** department PC:
   ```bash
   ping 192.168.40.1
