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
## 📡 IP Addressing Scheme (VLAN Subnets)

| VLAN Name       | VLAN ID | Subnet          | Default Gateway IP |
|-----------------|---------|------------------|---------------------|
| Management      | 10      | 10.0.10.0/24     | 10.0.10.1           |
| HR              | 20      | 10.0.20.0/24     | 10.0.20.1           |
| Finance         | 30      | 10.0.30.0/24     | 10.0.30.1           |
| Business        | 40      | 10.0.40.0/24     | 10.0.40.1           |
| Engineering     | 50      | 10.0.50.0/24     | 10.0.50.1           |
| Art & Design    | 60      | 10.0.60.0/24     | 10.0.60.1           |
| Student Labs    | 70      | 10.0.70.0/24     | 10.0.70.1           |
| IT Department   | 80      | 10.0.80.0/24     | 10.0.80.1           |
| Health Staff    | 90      | 10.0.90.0/24     | 10.0.90.1           |
| Health Students | 100     | 10.0.100.0/24    | 10.0.100.1          |

---

## 🛠️ Step-by-Step Configuration Guide

### 🔹 VLAN Configuration

```bash
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name Management
Switch(config)# vlan 20
Switch(config-vlan)# name HR
...
Switch(config)# exit
Switch(config)# interface range fa0/1 - 5
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 10
Switch(config)# ...
```
### 🔹 Inter-VLAN Routing (Router-on-a-Stick)
```bash
Router> enable
Router# configure terminal
Router(config)# interface g0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 10.0.10.1 255.255.255.0
...
```
Repeat for all VLANs: g0/0.20, g0/0.30, etc.

### 🔹 DHCP Configuration on Router
```bash
Router(config)# ip dhcp excluded-address 10.0.10.1 10.0.10.10
Router(config)# ip dhcp pool Management
Router(dhcp-config)# network 10.0.10.0 255.255.255.0
Router(dhcp-config)# default-router 10.0.10.1
...
```
Repeat for all VLANs.

### 🔹 RIP v2 Routing
```bash
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# no auto-summary
Router(config-router)# network 10.0.0.0
```
### 🔹 Static Route to Cloud Email Server
```bash
Router(config)# ip route 172.16.0.0 255.255.0.0 192.168.1.2
```
## 🔐 Security Configuration
### SSH Access on Switches
```bash
Switch(config)# hostname SW1
Switch(config)# ip domain-name abcuniversity.edu
Switch(config)# crypto key generate rsa
Switch(config)# username admin privilege 15 secret cisco123
Switch(config)# line vty 0 4
Switch(config-line)# login local
Switch(config-line)# transport input ssh
```
### Port Security
```bash
Switch(config)# interface fa0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport port-security
Switch(config-if)# switchport port-security maximum 1
Switch(config-if)# switchport port-security violation restrict
Switch(config-if)# switchport port-security mac-address sticky
```

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
