# Multi-Branch Office Network Setup

## Overview
This project involves setting up a scalable network for two office branches located in different cities using **Cisco Packet Tracer**. The setup includes **subnetting, static routing**, and **Port Address Translation (PAT)** to ensure seamless inter-branch communication and secure internet access.

## Authors
- <a href="https://github.com/SOMNATH0904">Somnath Shaw</a>
- <a href="https://github.com/DEBASISH077">Debasis Patra</a>

## Network Configuration Details

### 1. Subnetting
- Each branch is assigned a unique subnet.
- The subnets are structured to optimize IP address allocation.
- The subnet mask is configured to accommodate the required number of hosts per branch.

### 2. Static Routing
- Static routes are manually configured to establish communication between the two branches.
- Each branch router has static routes pointing to the opposite branch network via a WAN link.

### 3. Port Address Translation (PAT)
- PAT is implemented to allow multiple devices within a branch to access the internet using a single public IP address.
- The router is configured to translate private IP addresses to a single public IP dynamically.

## Implementation Steps

### Step 1: Network Topology Setup
- Add required network devices (routers, switches, PCs) in **Cisco Packet Tracer**.
- Assign appropriate IP addresses to each device according to the subnetting scheme.

### Step 2: Configuring Static Routing
On **Branch 1 Router**:
```cisco
ip route [Branch2_Network] [Subnet_Mask] [Next_Hop_IP]
```
On **Branch 2 Router**:
```cisco
ip route [Branch1_Network] [Subnet_Mask] [Next_Hop_IP]
```

### Step 3: Enabling PAT
On the router connected to the internet:
```cisco
access-list 1 permit [Internal_Network] [Wildcard_Mask]
ip nat inside source list 1 interface [Public_Interface] overload
interface [Internal_Interface]
 ip nat inside
interface [Public_Interface]
 ip nat outside
```

### Step 4: Testing Connectivity
- Use the **ping** command to verify communication between branches.
- Test external internet access from internal devices.

## Tools Used
- **Cisco Packet Tracer**

## Conclusion
This project successfully establishes a **multi-branch office network** with inter-branch communication and secure internet access using **subnetting, static routing, and PAT**. The setup ensures efficient and scalable network management for business operations.


