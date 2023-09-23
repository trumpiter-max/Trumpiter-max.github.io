---
title: "Intrusion detection & prevention system"
permalink: /security-wiki/blue-team/intrusion-detection-prevention-system/
excerpt: ""
---

# Introduction

## Basic definations

- **Intrusion**: access into the system without permission.
- **Evidence:**
    - **System logs** are short and missing.
    - The performance of the system is low, or work not correctly.
    - Crash or reboot (hard to detect).
- Detect: track, analyze, and know the evidence.
- **IDS**: Intrusion Detect System - an automatic system that detects, and analyzes attacks, is suited for testing system.
- **IPS**: Instrusion Prevent System - has all functions of IDS but it can be used for stop service, which is suit for the product. Moreover, **IDS/IPS** are the same system but have different functions, so IPS with removing prevent function can be used as IDS and vice versa.
- **IDPS** can be known as a system with IDS and IPS.
- **DPI** (Deep packet inspection): analyze secure requests in IDPS.
- **Network zone**:
    - **External** zone: not belong to the organization.
    - **DMZ**: belong to the organization being accessed from outside.
    - **Server farm**: belong to the organization, only access from local.
    - **Internal** zone: local machine.

## Basic detecting techniques

- **Signature-based** (both NIDPS and HIDPS):
    - Pros: depend on typical identity, using the known list of indicators of compromise (IOCs). Detecting known attacks quickly.
    - Cons: slow or can not detect alternative attacks which are different from the given list.
- **Anomaly-based** (both NIDPS and HIDPS):
    - Pros: depend on anomaly activities on the system, can detect attacks without any given list.
    - Cons: percentage of misidentification is still high
- **Specification-based** (NIDPS):
    - Pros: depend on the specification (standard) of the program or hardware as the point of reference, detect attacks quickly if they commit security policy.
    - Cons: depend on the manufacturers, difficult to modify in advanced.
- **Hybrid** (NIDPS):
    - Pros: using multiple above techniques to improve detecting speed.
    - Cons: complicated, can be cost-ineffective.
- **Heuristics-based** (HIPDS):
    - Pros: detect general features used by malware.
    - Cons: hard or can not detect unique/new malware.
- **Behavior-based** (HIPDS):
    - Pros: depend on suspect behavior.
    - Cons: can be bypassed.

**Notes**: The difference of IDPS and **AV(Anti Virus)**: IDPS is based on exploit (suite for system with multiple machines) and AV is based on file (suite for single machine, personal use).

**IDPS** has both open-source version and commercial version:

- Open-source:

    - Snort.
    - Zeek (aka Bro).
    - Suricata.
    - Security Onion.
- Commercial:

    - Kaspersky IoT Infrastructure Security.
    - Bitdefender GravityZone.

## Network-based 

There are threats and attacks in **TCP & UDP** such as session hijacking, ping-pong attacks, DoS attacks, and so on **Network-based IDPS** can monitor network segments and is deployed at **edge network**s. Used to analyze application (read data, protocol), transport, and network layer regularly

Main components:

- Sensor: 

  - **Hardware-based**: specific hardware (Ex: NIC), firmware, OS.
  - **Software-based**: OS or software
  - Deploy:
    - **Inline**: network flow goes through sensors (real-time) and can prevent attacks by blocking, located at the firewall, edge network where have is safe and less traffic.
    - **Passive**: monitor copy of network flow (not real-time), located at key parts in the network or essential segment (Ex: DMZ).

- Manager server.
- Console.
- Database server (optional). 

**Notes**: promiscuous mode in NIC: capture all packets frame from the network to the kernel, it has another name in Wifi: Monitor Mode.

### Monitor methods

- **Network TAPs** (Terminal Access Point) copy into IDPS: 

  - Pros: directly connect sensors to physics line, supply copy of network flow, fail-safe.
  - Cons: cost-ineffective.

- **Switch Port mirroring**:

  - Pros: switch copy frames of 1 or more ports sending to SPAN(Switch Port Analyzer).
  - Cons: if the **SPAN port** is misconfigured or overloaded, it may lose some traffic.
  
### Monitor tools

- **Protocol analyzer**: Wireshark, Tcpdump, etc.
- **NetFlow**: supply basic information of all IP flow forward to a device.
- **SIEM - Security Information Event Management**: report, and analyze real-time security events.
- **SNMP – Simple Network Management Protocol**: gather information of all network devices in passive.

Security ability:

- Gather information.
- Logs.
- Detect attacks.
- Prevent attacks.

## Host-based

**Monitoring events** in the host to detect suspect activities including:

- Network traffic.
- System log, process, file action, registry, etc.
- Rate host traffic.
- Not sniff packets when they go inside LAN.

**Endpoint Security**: 2 components of the network should be protected:

- **Endpoint**: hosts (Ex: laptop, pc, printer, etc.).
- **Network Infrastructure**: device used to connect hosts (Ex: switch, router, etc.).

There are 4 steps: Discover → Inventory → Monitor → Protect including Host-based security: AV(antivirus), anti-phishing, safe browsing, Host-based intrusion prevention system (HIDPS), firewall, and log.

**Host-based firewall**: control in/outbound traffic to the machine:

- **Window firewall**: profile-based firewall on Window.
- **Iptables**: same above but for Linux → **Nftables**: inheritance from Iptable (cleaner) and using the simple virtual machine in the kernel of Linux.
- **TCP Wrapper**: control access and log following rules on Linux.

Main components:

- **Agent**: same as **Sensor of NIDPS**, monitor one host and send reports to the server, designed to protect where can be accessed from the Internet or have sensitive data including the server, client, and service application. Being encrypted to prevent sniffing while processing sensitive data, the inline **agent** is deployed in front of the host.

### Host architecture

- Focus:

  - Pros: require fewer physics resources, performance is stable.
  - Cons: alert is not real-time.

- Dispersal:

  - Pros: real-time analysis and alert.
  - Cons: need more physics resources, performance can decrease efficiency.

## Security Monitoring

Collect and analyze data to detect anomaly behavior to alert, and do actions.

Other names:

- Security Information Monitoring (SIM).
- Security Event Monitoring (SEM).

## Machine/Deep Learning

A new solution to detect new attacks or bypass techniques. Using **signature-based** and **anomaly-based** methods to detect.

Machine learning algorithms need:

- Input is training dataset.
- Output is a model in which algorithms get new input and predict output.

**Supervised** learning (using labeled data):

- **Classification**:

  - Twice layers (Ex. detect attacks or normal) 
  - Multiple layers (Ex. detect malware is ransomware, key‐logger, or remote access trojan
)
- **Regression** (Anomaly-based): predict a float value (Ex. predict how many spam mails in one month)

**Unsupervised** learning (using unlabeled data):

- **Clustering**: detect similar data (Ex. detect anomaly large traffic caused by a botnet or normal users)

Others:

- **Semi-Supervised** Learning: including labeled and unlabeled data.
- **Reinforcement** Learning: based on an action-reward technique to make the agent try to do tasks in the environment and fail.

3 main steps:

- Preprocess: standardizing, encoding, normalizing, data cleaning, splitting the dataset into training and testing ( 80% - 20%).
- Training: make model.
- Testing: validate the model with the test dataset.

### Overfitting & Underfitting

- **Overfitting**:  

  - Pros: optimize detection if test cases are as the same as the training dataset.
  - Cons: can not detect new test cases which is different from the training dataset.

- **Underfitting**:

  - Pros: simple.
  - Cons: same as **Overfitting** because it is too simple.

Popular algorithms for machine learning:

- Decision Tree (DT).
- K-Nearest Neighbor (KNN).
- Support Vector Machine (SVM).
- K-Means Clustering.
- Ensemble Methods.
- **Shallow** Learning - Artificial Neural Network (ANN).
- Is supervised learning like the human neuron network.
- Including multiple neurons (nodes) and links.
- Using backpropagation.
- **Ensemble** learning: using multiple classifiers and voting.

Popular algorithms for deep learning:

- Convolutional neural network (CNN).
- Recurrent Neural Networks (RNN).
- AutoEncoder (AE).
- Deep belief network (DBN).

Rating index:

- Accuracy.
- False positive rate (FPR) and false negative rate (FNR).
- Precision.
- Recall (R - detection rate).
- F1-score.