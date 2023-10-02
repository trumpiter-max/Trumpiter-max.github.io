---
title: "Network insfrastrucure"
permalink: /security-wiki/network/network-insfrastrucure/
excerpt: ""
---

## Introduction

- **Network insfrastrucure** includes many network devices to transmist *packets* among all devices (end-device, access point, server, ...) with wires, wireless (radio).
- **Network service** includes applications handling requests, responses from users and servers.

## Router

### Compoments: 

- **CPU** controls activities of router.
- **RAM** includes **running-config**( save all own configures). 
- **Flash** (OS data).
- **NVRAM** includes **startup-config** (copy all data from running-config for next startup).
- **Interface**: **Management** (Console, MiniUSB, AUX), **LAN**(GigaEthernet - over 1GB/s, FastEthernet- over 100MB/s), **WAN** (Serial).
- Leds: show status of services of router.

### Roles:

#### LAN segementation

A network area (broadcast domain) connect to per network interface.

#### Router

##### Routing (Control plane)

- Build and maintains a routing table (network map) to forward packet to other routers in network.
- Directed network automatically or manually (static routes).
- Network protocols include **connected** which connect to router directly and **learned** which not connect to router over protocol.
- Control with software or protocol.

##### Forwarding (Data plane)

Collecting data from one device and sending it to another device.

##### Routing process

Selecting and defining paths for **IP-packet traffic** within or between networks as well as the process of managing network traffic overall. Administrative distance (AD) or route preference is a number of arbitrary unit assigned to dynamic routes, static routes and directly-connected routes.

##### Routing protocol selection

- Network size: complex network, a number of devices,...
- Vendor interoperability: hardware support.
- Speed of convergence: the speed routing learning new paths after incidents happen in network.
- Interior or extorior routing: rent outside ISP or do own ISP.
- Type of routing protocol: require engineers' skills. 

##### Routing table structure

Source of learned routing information:

- (L) Local Route interfaces.
- (C) Directly connected interfaces.
- (S) Static routes.
- (R) Learned dynamically via the RIP routing protocol.
- (D) Learned dynamically via the EIGRP routing protocol.
- (O) Learned dynamically via the OSPF routing protocol.

Routing table entries:

- Route source.
- Destination network.
- Administrative distance.
- Metric.
- Next-hop.
- Route timestamp.
- Exit interface.

### Data transmission over LAN

- **Switch** transmists data among network interfaces.
- **Switching table** includes **network interface** and **MAC address** to forward packets to router.
- When a machine want to send data to others machine, it will use **ARP** to find right addresses (IP - logical or MAC - physical).

#### Subnet
    
- **Subnets** make networks more efficient, travel a shorter distance without passing through unnecessary routers to reach its destination.
- **Subnet mask** is defined as a *32-bit address* that segregates an *IP address* into network bits that identify the network and host bits that identify the host device operating on that network. For example, popular **subnet mask** is `255.255.255.0` allowing up to 254 usable IP addresses in LAN. From below sample, the subnet *borrows 2 bits*. There are some default configures:

|Class name | Public IP  | Private IP  | Subnet | Subnet mask  |
|---|---|---|---|---|
| A | 1.0.0.0 to 127.0.0.0 | 10.0.0.0 to 10.255.255.255 | 255.0.0.0 | /8 |
| B | 128.0.0.0 to 191.255.0.0 | 172.16.0.0 to 172.31.255.255 | 255.255.0.0 | /16 |
| C | 192.0.0.0 to 223.255.255.0 | 192.168.0.0 to 192.168.255.255 | 255.255.255.0 | /24 |

/8: means network octet includes 8 bit 1.

**Notes**: If the machine use **static IP** but isn't assigned **stactic IP** and can't connect or find **DHCP server**, it will be assigned automatically with IP from **169.254.0.1** to **169.254.255.254**, this will prevent the machine connect to others in network or connect to the Internet.

![Sample subnet mark](/resources/images/collection/network-and-host-bits-2.png)

##### Variable length subnet masking

To calculate the number of possible subnets, use the formula **2<sup>n</sup>,** where n equals the number of *host bits borrowed* (bit 1). For example, n=3. 2<sup>3</sup> = 8. 

Then calculate remaininng bits (bit 0) to find out the **number of host/subnet = 2<sup>m</sup> - 2** (except NetID and Broadcast address):

```
    m = 32 - n - number of current subnet mask (A - 8, B - 16, C - 24)
```  

To calculate the number of **hops = 2<sup>m</sup>**, **New subnet mask = 256 - hops**.

**Subnet ID** includes:

- First subnet ID = 0.
- Next subnet ID = Current Subnet ID + hops.

Inside one subnet ID:

- First host = subnet ID + 1.
- Last host = subnet ID + hops - 2.
- Broadcast address = Last host + 1.

#### Static routing

Using a **manually-configured** routing entry, the IP of machines will not change. It is used for small networks, routing to and from stub networks, using a single default route:

- Pros: not advertised, less resoures, make network more security, route is known.
- Cons: more time-consuming, effort for configure, maintainance, and scaling.

**Note**: the machine uses static IP need to set up **default gateway** (IP of interface router) for sending data to router. For connecting the Internet, the machine need setting up default network (0.0.0.0).

Types of static routers:

- **Standard**: route for determined static routes.
- **Default**: used for determining paths of packets while there is no information on packets. Destination is 0.0.0.0/0 in IPv4.
- **Summary**: summary other consecutive static routes for routing tables which have same exit gates or next router.
- **Floating**: backup static routes if any main static routes can't used.

Syntax for static configure:

```sh
    ip route destination-address subnet-mask {next-hop-address-or-outbound-interface} [distance] (default distance for static route is 1)
```

Direct connections to router are recognized by router. **Next-hop address** means the IP address of the next router's port having direct connection. **Outbound interface** means the destination port which router sends data.

#### Dynamic routing - RIP

- Routers share updates between neighbors. 
- Sending updates to multicast or broadcast IP 255.255.255.255 or 224.0.0.9 (depend on protocol).
- Protocol: RIP, IGRP, RIPv2, EIGRP, OSPF.

##### Distance vector algorithm

- **RIP** uses the **Bellman-Ford** algorithm as its routing algorithm.
    - Sending and receiving routing information.
    - Calculating the best paths and installing routes in the routing table.
    - Detecting and reacting to topology changes.
- Routing updates broadcasted every 30 seconds, using **UDP port 520**.
- **RIPv2** has more features than v1:
  - Support **VLSM** & **CIDR**.
  - Support authentication.

Syntax for **RIPv2** configure:

```sh
    router ip
    version 2
    network {ip-machine} # enable RIP on interface advertises the specific network.
    passive-interface {interface} # prevent sending out unneed updates on LAN.
    default-information originnate
```



