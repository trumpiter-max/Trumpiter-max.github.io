---
title: "Network security"
permalink: /security-wiki/network/network-security/
excerpt: ""
---

# Introduction

This session is based on the triad: **confidentiality**, **integrity**, **availability**:

- **Confidentiality**: prevent from leaking information without permission.
- **Integrity**: prevent from changing information without permission.
- **Availability**: make sure the valid users can access information and the system.

Moreover, 2 other security goals:

- Authenticity: ensure data comes from trust and legal source.
- Accountability: store logs, tracking.

## Vulnerability, threat, risk

- Vulnerability: the weaknesses of system which
- Threat: new accident (or zero-day) can be harmful for all system or company.
- Risk: can loss or damage when threat exploit vulnerabilities.

## Attack and coutermeasure

- Attack is the threat which can lead to  unwanted violations of protection confidentiality or the consequences of the threat.
    - Active: attempt to change system resources, or work.
    - Passive: use information from system without affecting system resources.
- Coutermeasure: prevent or mitigate, recovery effects of attacks.

### Some types of attacks

- Unauthorized disclosure:
  
  - Expose.  
  - Interception.
  - Inference.
  - Intrusion.

- Deception:

  - Masquerade.
  - Falsification.
  - Repudiation.

- Disruption:

  - Incapacitation.
  - Corruption.
  - Obstruction.

- Usurpation:

  - Misappropriation.
  - Misuse.

## Security design principles

- **Economy of mechanism**: keep the design as simple and small as possible.  
- **Fail-safe defaults**: unless a subject is given explicit access to an object, it should be denied access to that object.  
- **Complete mediation**: requiring access requests to be mediated every time, to avoid authority being circumvented through multiple requests.  
- **Open design**: a system security shouldn't rely on the secrecy of its implementation.  
- **Separation of privilege**: requires multiple people to approve an action before it can be completed. 
- **Least privilege**: a security architecture should be designed so that each entity is granted the minimum system resources and authorizations.  
- **Least common mechanism**: mechanisms used to access resources should not be shared. 
- **Psychological acceptability**: security mechanisms should not make the resource more difficult to access than if the security mechanisms were not present.
- **Isolation**: public access systems should be separated from critical resources (data, processes, etc.) to prevent disclosure or tampering.
- **Encapsulation**: the protected system can only access the data object of the system and these processes can only be invoked from a domain entry point. 
- **Modularity**: the security mechanism must be generated as separate and protected modules and the security mechanism must be generated using the modular architecture.
- **Layering**: use of multiple, overlapping protection approaches 
addressing the people, technology, and operational aspects of information systems
- **Least astonishment**: should avoid surprising users (in an unpleasant way) at any cost.