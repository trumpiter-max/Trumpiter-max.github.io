---
title: "Network introduction"
permalink: /security-wiki/network/network-introduction/
excerpt: "First objects for knowing network"
---

## Basic definitions

- **Protocol**:  rules to send and receive, define the format, and order.
- **Network edge/end system**:  networks used in the house, school, ... and *devices edge* are laptops, smartphones, smart tv, etc.
- **Internet**: the network of networks, including many connected computers all over the world. 
- **Router**: a device used for forwarding packets in the network. The router is used by LAN as well as MAN.
- **Switch**: a device is used for gathering many devices locally and connecting the end devices. The switch is used by only LAN.
- **bps**: bits per second, a popular unit for measuring network speed.

### Store & Forward

**Store & Forward** is all packets that should be delivered to the router before those are transmitted to next part.

It takes `L/R seconds` per hop for transmitting an L-bit packet with R bps. So if the latency when a send packet from source to destination with 2 hops takes `2L/R` seconds. 

End-end delay = `2L/R + D1/c + D2/d` caused by spread delay. D1, D2 is the length of the link; c, d is the spread speed.

### Alternative core

Equally divided resource for connecting between source and destination:

- **FDM**: all connections are parallel and have no queue. Using a channel per connection.

- **TDM**: all connection in the queue and no parallel. Resource usage per connection in limit time.

**Circuit switching**: data is transmitted followed by a router until the end connection
 - Pros: stable, with little latency or loss
 - Cons: more time-consuming connect initialization, performance not high.
 - The maximum number of connections at any one time is the total of connections. In this case, this is 65 circuit.
 - When the connection is full, it will block another connection that wants to join in.

**Packet Switching**: divide data into the packets application layer:

- Pros: high performance.
- Cons: more packets more time-consume, high loss rate.

## Reasons cause the delay in network

The *delay time* is equal to the total of reasons below: 

- Process at node.
- Queue.
- Transmit, length.
- Spread in the environment `(~2x10^8 m/s)`.

### Throughput & Bandwidth

**Bandwidth**: the maximum amount of data transmitted over an internet connection in a given amount of time.

**Throughput**: transmiting speed (bits/time unit) between source and destination. 

## OSI Model

Using for simplifying network, easy to understand the relation and maintain, update network. 

There are 7 layers in OSI:

- Layer 7: Application has HTTP, FTP, Telnet, SMTP, DNS.
- Layer 6: Presentation.
- Layer 5: Session.
- Layer 4: Transport has TCP, UDP.
- Layer 3: Network has IP.
- Layer 2: Link.
- Layer 1: Physics.

### Application

 - Website.
 - Mobile application.

### Presentation

 - Apple Filing Protocol (AFP): Apple Filing Protocol. 
 - Lightweight Presentation Protocol (LPP): Lightweight Presentation Protocol. 
 - NetWare Core Protocol (NCP): NetWare Core Protocol. 
 - Network Data Representation (NDR): Network Data Representation. 
 - External Data Representation (XDR): External Data Representation (XDR). 
 - Secure Socket Layer (SSL): The Secure Socket Layer (TLS is safer than SSL).

### Session

 - AppleTalk Data Stream Protocol (ADSP).
 - Real-time Transport Control Protocol (RTCP).
 - Point-to-Point Tunneling Protocol (PPTP).
 - Password Authentication Protocol (PAP).
 - Remote Procedure Call Protocol (RPCP).
 - Sockets Direct Protocol (SDP): Sockets Direct Protocol (SDP).

### Transport

 - TCP/IP is the Transmission Control Protocol (TCP).
 - User Datagram Protocol (UDP). 
 - Datagram Congestion Control Protocol (DCCP).
 - Stream Control Transmission Protocol (SCTP).

### Network 

 - Forwarding.
 - Routing.
 - Virtual circuit network. 
 - Datagram network.

### Link

 - LLC (logical link control) và MAC (Media Access Control).
 - Switch.

### Physics

- NIC (Network interface card).