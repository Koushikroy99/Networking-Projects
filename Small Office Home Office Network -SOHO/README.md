<p align="center">
    <img src="./cisco-logo.png" alt="Logo" width="200">
</p>

<h2 align="center"> NETWORKING PROJECTS</h2>

## About this project

This repository contains a collection of networking labs and simulation projects created using Cisco Packet Tracer. These labs demonstrate real-world scenarios in networking, including VLAN setup, Inter-VLAN routing, DHCP configuration, and wireless setup. In this particular project, we have designed a Small Office/Home Office (SOHO) network that includes wired and wireless connectivity for multiple departments, secure VLAN-based segmentation, and centralized IP management using DHCP.

## Networking Labs

### 1. Small Office Home Office Network - SOHO

<p align="center">
    <img src="./Small Office Home Office Network -SOHO.png" alt="Small Office Home Office Network -SOHO">
</p>

<details>
<summary><strong>⚙️ Steps to Configure the Network (Small Office Home Office Network - SOHO)</strong></summary>

<br>

## 🏢 JMD Agro Foods Pvt. Ltd. – Branch Office SOHO Network Design & Implementation

### 📍 Location: Bonalbo Village, West Bengal, India

**JMD Agro Foods Pvt. Ltd.** is a rapidly growing Indian company engaged in the **procurement and distribution of food products** across India. With over 2 million customers and operations managed from its **headquarters in Kolkata**, the company is expanding by opening a **new branch in Bonalbo village**, West Bengal. For this branch, the company requires a robust and scalable **SOHO (Small Office/Home Office)** network setup.

As a newly recruited network engineer, you have been assigned to **design and implement the SOHO network** infrastructure, ensuring secure, reliable communication among departments with wireless access and automated addressing.

---

### 🏠 What is SOHO?

**SOHO (Small Office/Home Office)** refers to a compact network designed for smaller business environments. It supports essential services like wired/wireless access, DHCP, VLAN segregation, and inter-device communication—ideal for small teams and startups.

---

### 📋 Project Requirements (SOHO Branch Setup)

✅ Use of **1 Cisco Router** and **1 Cisco Switch**  
✅ Creation of **3 Departments**:
- Admin / IT
- Finance / HR
- Customer Service / Reception

✅ Each department must:
- Be assigned to a **separate VLAN**
- Have dedicated **wireless access (WiFi)**
- Receive IP addresses **automatically via DHCP**

✅ Devices in all departments must be able to **communicate with each other**  
✅ ISP-provided base network: `192.168.1.0/24`

---

### ⚙️ Technologies Implemented in SOHO Setup

- Network Design using **Cisco Router and Access Layer Switch**
- **Correct Cabling** between networking devices
- **VLAN Configuration** and port mapping
- **Subnetting & IP Addressing**
- **Router-on-a-Stick (Inter-VLAN Routing)**
- **DHCP Server Setup** (Router as DHCP Server)
- **WLAN Configuration** (Wireless Network using Cisco APs)
- **Host Device Configuration**
- **Testing & Troubleshooting** for network performance

---

### 🧩 SOHO Network Design Summary

#### 🔗 Devices Used

- **1 Cisco Router**
- **1 Cisco Switch**
- **3 Cisco Access Points**
- **9 End Devices (PCs, Laptops)**
- **Copper Straight-Through Cables**

---

### 🧱 VLANs & Department Mapping (SOHO Zones)

| Department                | VLAN ID | IP Subnet         | VLAN Name          |
|--------------------------|---------|-------------------|--------------------|
| Admin / IT               | 10      | 192.168.1.0/27    | VLAN10_ADMIN_IT    |
| Finance / HR             | 20      | 192.168.1.32/27   | VLAN20_FINANCE_HR  |
| Customer Service / Front | 30      | 192.168.1.64/27   | VLAN30_CUSTOMER    |

---

### 🌐 IP Addressing Plan (SOHO Subnets)

| VLAN | Subnet             | Default Gateway     | DHCP Range                  |
|------|--------------------|---------------------|-----------------------------|
| 10   | 192.168.1.0/27     | 192.168.1.1         | 192.168.1.2 – 192.168.1.30  |
| 20   | 192.168.1.32/27    | 192.168.1.33        | 192.168.1.34 – 192.168.1.62 |
| 30   | 192.168.1.64/27    | 192.168.1.65        | 192.168.1.66 – 192.168.1.94 |

---

### 🛠️ Key Configuration Steps

#### 1️⃣ VLAN Configuration on Switch
```bash
Switch(config)# vlan 10
Switch(config-vlan)# name VLAN10_ADMIN_IT

Switch(config)# vlan 20
Switch(config-vlan)# name VLAN20_FINANCE_HR

Switch(config)# vlan 30
Switch(config-vlan)# name VLAN30_CUSTOMER
```
#### 2️⃣ Port Assignments per VLAN
```bash
Switch(config)# interface range fa0/1 - 3
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 10

Switch(config)# interface range fa0/4 - 6
Switch(config-if-range)# switchport access vlan 20

Switch(config)# interface range fa0/7 - 9
Switch(config-if-range)# switchport access vlan 30
```

#### 3️⃣ Trunk Port to Router
```bash
Switch(config)# interface fa0/24
Switch(config-if)# switchport mode trunk
```
### 🖧 Router Configuration for Inter-VLAN Routing
```bash
Router(config)# interface gig0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.1.1 255.255.255.224

Router(config)# interface gig0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.1.33 255.255.255.224

Router(config)# interface gig0/0.30
Router(config-subif)# encapsulation dot1Q 30
Router(config-subif)# ip address 192.168.1.65 255.255.255.224
```
### DHCP Configuration
```bash
Router(config)# ip dhcp pool VLAN10
Router(dhcp-config)# network 192.168.1.0 255.255.255.224
Router(dhcp-config)# default-router 192.168.1.1

Router(config)# ip dhcp pool VLAN20
Router(dhcp-config)# network 192.168.1.32 255.255.255.224
Router(dhcp-config)# default-router 192.168.1.33

Router(config)# ip dhcp pool VLAN30
Router(dhcp-config)# network 192.168.1.64 255.255.255.224
Router(dhcp-config)# default-router 192.168.1.65
```
---
### 📡 Wireless Access Points Configuration

Each Access Point should be configured with the following details for respective departments:

| VLAN | Department                | SSID                | VLAN ID | Security Type | Password       |
|------|---------------------------|---------------------|---------|----------------|----------------|
| 10   | Admin / IT                | JMD_Admin_WiFi      | 10      | WPA2-PSK       | admin@123      |
| 20   | Finance / HR              | JMD_Finance_WiFi    | 20      | WPA2-PSK       | finance@123    |
| 30   | Customer Service / Front  | JMD_Customer_WiFi   | 30      | WPA2-PSK       | customer@123   |

#### 🔧 Example Configuration (GUI - Cisco Packet Tracer)

1. Click the Access Point  
2. Go to the **Wireless** tab  
3. Add new SSID Name (e.g., `JMD_Admin_WiFi`)  
4. Enable **Broadcast SSID**  
5. Assign VLAN ID (e.g., `10`)  
6. Set Authentication to **WPA2-PSK**  
7. Enter Passphrase (e.g., `admin@123`)  
8. Repeat for VLAN 20 and VLAN 30 with their corresponding SSIDs and VLAN IDs  

#### 🧪 Testing Wireless Configuration

- Connect a wireless laptop or PC to each SSID.  
- Verify IP assignment using `ipconfig` (should match the subnet for its VLAN).  
- Ping default gateway (e.g., `192.168.1.1` for Admin).  
- Test internet access or inter-VLAN connectivity if permitted.
