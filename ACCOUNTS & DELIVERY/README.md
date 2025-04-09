<p align="center">
    <img src="./cisco-logo.png" alt="Logo" width="200">
</p>

<h2 align="center"> NETWORKING PROJECTS</h2>

## 📝About this project

In this project, we are configuring a network for two departments — Accounts and Delivery. The network is divided using subnetting, and communication is established through proper IP addressing and physical connections.

## Networking Labs

### 1. Network Design for ACCOUNTS & DELIVERY Departments

<p align="center">
    <img src="./1. Accounts &Delivery Lab.png" alt="ACCOUNTS & DELIVERY">
</p>

<details>
<summary><strong>⚙️ Steps to Configure the Network (Accounts & Delivery Departments)</strong></summary>

<br>

## 🧩 Network Topology:
- **1 Router** (using GigabitEthernet0/0 and GigabitEthernet0/1)
- **2 Switches** (one for each department)
- **4 PCs** (2 in Accounts, 2 in Delivery)
- **Copper Straight-Through Cables** used for all connections

---

## 🏢 Department Structure:

### 📂 Accounts Department:
- **PC1**
- **PC2**

### 🚚 Delivery Department:
- **PC3**
- **PC4**

---

## 🌐 IP Addressing & Subnetting:

- **Main Network:** `192.168.40.0/24`
- **Subnetting:** 1 borrowed bit → `255.255.255.128 (/25)`
- **Total Subnets:** 2

### Subnet 1 – Accounts:
- **Network ID:** `192.168.40.0`
- **Broadcast Address:** `192.168.40.127`
- **Usable Host Range:** `192.168.40.1 – 192.168.40.126`

### Subnet 2 – Delivery:
- **Network ID:** `192.168.40.128`
- **Broadcast Address:** `192.168.40.255`
- **Usable Host Range:** `192.168.40.129 – 192.168.40.254`

---

## 🛠️ Step-by-Step Configuration

### 🔌 1. Physical Setup in Cisco Packet Tracer
- Drag and drop:
  - 1 Router
  - 2 Switches
  - 4 PCs (2 for each department)
- Connect devices using **copper straight-through cables**:
  - Router Gig0/0 to Accounts Switch
  - Router Gig0/1 to Delivery Switch
  - PCs to their respective department switches

---

### 🌐 2. Configure the Router

```bash
Router> enable
Router# configure terminal

Router(config)# interface gigabitEthernet0/0
Router(config-if)# ip address 192.168.40.1 255.255.255.128
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface gigabitEthernet0/1
Router(config-if)# ip address 192.168.40.129 255.255.255.128
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# exit
```

### 💻 3. Configure IPs on Each PC

➡️ Navigate to: `PC > Desktop > IP Configuration` and manually assign IP addresses as follows:

### 🧾 Accounts Department:
**PC1**  
- IP Address: `192.168.40.10`  
- Subnet Mask: `255.255.255.128`  
- Default Gateway: `192.168.40.1`

**PC2**  
- IP Address: `192.168.40.11`  
- Subnet Mask: `255.255.255.128`  
- Default Gateway: `192.168.40.1`

---

### 🧾 Delivery Department:
**PC3**  
- IP Address: `192.168.40.130`  
- Subnet Mask: `255.255.255.128`  
- Default Gateway: `192.168.40.129`

**PC4**  
- IP Address: `192.168.40.131`  
- Subnet Mask: `255.255.255.128`  
- Default Gateway: `192.168.40.129`

---

## 🧪 4. Connectivity Testing

➡️ Open the **Command Prompt** on each PC and run the following ping tests:

```bash
PC1 > ping 192.168.40.11      # Test between PCs in Accounts Department
PC1 > ping 192.168.40.130     # Test communication with Delivery Department
```

✅ Expected Result: All ping replies should be successfully received. This confirms that inter-department communication is functional and the network is properly configured.
