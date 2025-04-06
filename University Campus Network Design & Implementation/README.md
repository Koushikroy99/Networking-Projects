<p align="center">
    <img src="./cisco-logo.png" alt="Logo" width="200">
</p>

<h2 align="center"> NETWORKING PROJECTS</h2>

## 📝 About this Project

This project showcases the full design and implementation of a campus-wide network for **ABC University**, which has **two campuses** located 20 miles apart. The goal is to ensure reliable, scalable, and secure communication across all departments, faculties, and remote campuses using **Cisco Packet Tracer**.

## Networking Labs

### 3. 🎓 Campus Network Design & Implementation Project – ABC University
<p align="center">
    <img src="./University Campus Network Design & Implementation.png" alt="University Campus Network Design & Implementation">
</p>

<details>
<summary><strong>⚙️ Steps to Configure the Network (Small Office Home Office Network - SOHO)</strong></summary>

<br>

## 🏫 Network Overview

- **Main Campus**:
  - **Building A**: Admin departments (Management, HR, Finance) + Faculty of Business
  - **Building B**: Faculty of Engineering & Computing + Faculty of Art & Design
  - **Building C**: Student Labs + IT Department (hosts Web Server and internal services)

- **Smaller Campus**:
  - Faculty of Health & Sciences (Staff & Student Labs on different floors)

---

## 🔧 Technologies Implemented

- ✅ Cisco Packet Tracer-based network simulation
- ✅ Hierarchical Network Design
- ✅ Subnetting and IP Addressing
- ✅ VLAN Creation and Management
- ✅ Inter-VLAN Routing (Router-on-a-Stick)
- ✅ RIP v2 Routing Protocol (Internal Routing)
- ✅ Static Routing (External Cloud Email Server)
- ✅ Router-based DHCP Server for dynamic IP allocation
- ✅ SSH for secure remote access to devices
- ✅ Port Security on switches
- ✅ Cloud connectivity simulation

---

## 📡 IP Addressing Scheme

Each VLAN represents a separate subnet:
| VLAN Name         | VLAN ID | Subnet         | Interface IP       |
|------------------|---------|----------------|--------------------|
| Management        | 10      | 10.0.10.0/24   | 10.0.10.1          |
| HR                | 20      | 10.0.20.0/24   | 10.0.20.1          |
| Finance           | 30      | 10.0.30.0/24   | 10.0.30.1          |
| Business          | 40      | 10.0.40.0/24   | 10.0.40.1          |
| Engineering       | 50      | 10.0.50.0/24   | 10.0.50.1          |
| Art & Design      | 60      | 10.0.60.0/24   | 10.0.60.1          |
| Student Labs      | 70      | 10.0.70.0/24   | 10.0.70.1          |
| IT Department     | 80      | 10.0.80.0/24   | 10.0.80.1          |
| Health Staff      | 90      | 10.0.90.0/24   | 10.0.90.1          |
| Health Students   | 100     | 10.0.100.0/24  | 10.0.100.1         |

---

## 🔐 Security Features

- **SSH access** to switches for secure remote management
- **Port Security** enabled on user ports to prevent unauthorized access
- **DHCP Exclusions** to reserve gateway IPs
- **Separation of network traffic** via VLANs and subnets

---

## ⚙️ Configuration Components

- **VLANs** and port assignments on switches
- **Router-on-a-Stick** (subinterfaces for inter-VLAN routing)
- **DHCP Pools** per subnet
- **RIP v2** to share internal routing information
- **Static Route** to reach cloud-hosted Email Server
- **SSH + Port Security** for switch management
- **Tested Connectivity** via ping, traceroute, and console access

---

## 🧪 Testing & Verification

| Task                           | Command                        |
|--------------------------------|--------------------------------|
| View VLANs                     | `show vlan brief`             |
| View Routing Table             | `show ip route`               |
| Test IP Communication          | `ping <destination>`          |
| Check DHCP Address             | `ipconfig` on PCs             |
| Verify RIP                     | `show ip protocols`           |
| SSH to Switch                  | `ssh -l admin <switch IP>`    |
| Check Port Security            | `show port-security`          |

---

## 🗂 File Structure

