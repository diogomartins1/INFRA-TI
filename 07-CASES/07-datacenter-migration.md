# Case 07 — Datacenter Migration to Cisco ACI

## Context

Datacenter modernization initiative involving the migration of connectivity from an existing environment to a new datacenter designed around **Cisco ACI**.

The objective was to move infrastructure components to a more robust and controlled environment while preserving the required connectivity to the existing enterprise network.

## Existing Environment — As-Is

The existing environment included:

- Cisco Nexus 5000 switches;
- Cisco Nexus 7000 infrastructure acting as part of the existing network path;
- existing server connectivity;
- iSCSI storage connectivity;
- management interfaces such as iLO/iDRAC;
- existing uplinks between datacenter environments;
- Cisco ACI already deployed in the target/adjacent datacenter environment.

The planning material identified an existing **2 × 10 Gb/s uplink** between the relevant environments.

## Target Environment — To-Be

The target architecture introduced Cisco ACI leaf switches into the new datacenter environment.

The planned model connected the new servers and storage directly to the ACI leaf layer, with the ACI fabric integrating upstream through the existing Nexus infrastructure.

At a high level:

```text
                 Enterprise / Existing Network
                           │
                     Nexus 7000
                       VPC / Trunk
                           │
                ┌──────────┴──────────┐
                │                     │
           ACI Leaf               ACI Leaf
                │                     │
          Servers / Storage / New Datacenter
```

## Technical Challenge

The migration required more than installing new switches. The existing connectivity had to be understood in detail before the target architecture could be defined.

The planning involved identifying:

- existing uplinks;
- available interfaces;
- server management connections;
- server data interfaces;
- iSCSI interfaces;
- storage interfaces;
- existing Nexus relationships;
- ACI connectivity;
- required capacity between the datacenter environments.

## Uplink Expansion

One of the identified requirements was increasing the existing uplink capacity from **2 × 10 Gb/s to 4 × 10 Gb/s**.

The planning included identifying available interfaces on the existing Nexus infrastructure and the corresponding interfaces on the upstream switch.

The expansion was intended to provide additional bandwidth and improve the connectivity capacity available to the new environment.

## Server and Storage Connectivity

The planning separated connectivity requirements by function rather than treating the server as a single network endpoint.

The environment included distinct requirements for:

- management interfaces;
- data interfaces;
- iSCSI/storage interfaces;
- future storage connectivity;
- network uplinks.

The planning material also identified interfaces to be reserved for future storage equipment, allowing cabling and infrastructure preparation to progress before all equipment was available.

## My Role

My contribution was focused on the **network infrastructure analysis and planning** required to support the migration.

Activities included:

- collecting the existing network information;
- mapping interfaces and connections;
- identifying available ports for expansion;
- documenting current server and storage connectivity;
- analyzing the existing Nexus topology;
- identifying the relationship between Nexus and Cisco ACI;
- planning the additional 10 Gb/s uplinks;
- defining connectivity requirements for servers and storage;
- supporting the As-Is / To-Be architecture documentation.

This work was primarily focused on **infrastructure planning and implementation preparation**, rather than operating as the sole owner of the complete datacenter migration.

## Planning Flow

```text
Existing environment inventory
          ↓
Interface and connectivity mapping
          ↓
Server / storage requirements
          ↓
Available port analysis
          ↓
Uplink capacity assessment
          ↓
As-Is architecture
          ↓
To-Be architecture with Cisco ACI
          ↓
Implementation and cabling planning
```

## Architecture Principles

### 1. Preserve existing dependencies

The target design needed to maintain connectivity with the existing enterprise network while introducing the new ACI-based environment.

### 2. Separate connectivity by function

Management, production/data and storage traffic were considered separately to make the connectivity requirements explicit.

### 3. Plan capacity before implementation

The uplink expansion from 2 × 10 Gb/s to 4 × 10 Gb/s was identified as part of the infrastructure preparation rather than being treated as an afterthought during migration.

### 4. Prepare for future equipment

Reserved interfaces allowed the infrastructure team to prepare cabling and port allocation before the arrival of additional storage equipment.

## Skills Demonstrated

- Cisco ACI
- Cisco Nexus 5000
- Cisco Nexus 7000
- VPC
- Trunk connectivity
- 10 Gb/s Ethernet
- Server networking
- iSCSI
- Storage connectivity
- Interface and port mapping
- Datacenter migration planning
- As-Is / To-Be architecture
- Technical documentation

## Technical Takeaway

A successful datacenter migration begins with a precise understanding of the existing connectivity model.

Before introducing a new fabric such as Cisco ACI, it is necessary to map the existing interfaces, uplinks, servers, storage, management paths and dependencies. This creates the technical foundation for defining the target architecture and executing the migration with controlled impact.

## Confidentiality

This case is intentionally generalized. Company-specific names, IP addresses, hostnames, serial numbers, exact port assignments and other operational identifiers have been omitted.

The architecture description represents the technical planning approach and target design at a non-confidential level and does not reproduce the production topology in full.
