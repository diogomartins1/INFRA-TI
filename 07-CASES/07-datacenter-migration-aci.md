# Case 07 — Datacenter Migration to Cisco ACI

## Context

Infrastructure modernization initiative for the migration of connectivity supporting the JB DC iNEWS environment to a new datacenter environment, referred to in the planning as **JB CED**.

The objective was to move the connectivity toward a newer and more robust datacenter architecture based on **Cisco ACI and Nexus**, while maintaining the required communication with the existing enterprise network and presidential environment.

## Starting Point

The existing environment had connectivity distributed across different network layers, including Nexus 5000 switches in the JB DC iNEWS environment and Nexus 7000 devices acting as part of the existing network/gateway architecture.

The planning material identified an existing uplink structure and several server/storage dependencies that needed to be understood before migration.

Examples included:

- Nexus 5000 connectivity;
- Nexus 7000 uplinks;
- existing server management and data interfaces;
- iSCSI storage connectivity;
- existing network segments already available in the corporate Nexus environment;
- downstream connectivity toward the presidential environment.

## Target Architecture

The target design introduced the new ACI-based datacenter into the connectivity path.

At a high level:

```text
                 Existing Enterprise Network
                           │
                     Nexus / Gateway
                           │
                         VPC
                           │
                    ┌──────┴──────┐
                    │ Cisco ACI   │
                    │   Fabric    │
                    └──────┬──────┘
                           │
                 ┌─────────┴─────────┐
                 │                   │
              Servers             Storage
                 │                   │
                 └─────────┬─────────┘
                           │
                      JB CED
```

The target architecture connected servers and storage directly to ACI leaf infrastructure, with the ACI fabric connecting upstream through a VPC-based design toward the existing Nexus 7000 gateway layer.

## Technical Challenge

The migration was more than a physical relocation of equipment. Existing services had dependencies on specific interfaces, VLANs, uplinks, management networks and storage paths.

The planning therefore required a detailed inventory of the existing environment and a mapping between the **As-Is** and **To-Be** architectures.

A key requirement was to expand the existing uplink capacity while introducing the new ACI-based connectivity.

The planning identified an existing **2 × 10 Gb/s** uplink and evaluated expansion to **4 × 10 Gb/s**.

## My Role

As a Networks/Telecom analyst, I participated in the technical planning of the connectivity migration.

My activities included:

- inventorying existing network equipment and interfaces;
- mapping current server and storage connectivity;
- identifying available interfaces for the migration;
- analyzing existing uplinks and capacity;
- planning additional 10 Gb/s links;
- identifying connectivity requirements for servers and storage;
- mapping management and data networks;
- evaluating the integration between the existing Nexus environment and the new ACI fabric;
- documenting the As-Is and To-Be architecture;
- coordinating technical dependencies required for cabling, equipment installation and commissioning.

## Existing Connectivity Analysis

The planning included detailed interface mapping of the existing Nexus 5000 and Nexus 7000 infrastructure.

For example, the JB environment contained existing 10 Gb/s trunk connections between the Nexus 5000 layer and the Nexus 7000 pair, as well as a VPC relationship between Nexus devices.

The analysis also identified existing server interfaces used for management and iSCSI, and storage interfaces connected to the Nexus 5000 infrastructure.

This inventory was necessary to understand which connections could be migrated, which needed to remain temporarily in place and which interfaces needed to be reserved for new equipment.

## Uplink Expansion

One of the identified requirements was increasing the uplink between the Nexus 7000 layer and the downstream switching environment.

The existing architecture had **2 × 10 Gb/s** connectivity. The target planning considered increasing this to **4 × 10 Gb/s**, improving aggregate capacity and providing a more suitable foundation for the new infrastructure.

The work involved identifying available interfaces on the relevant switches, validating physical connectivity options and considering the impact of the change on the existing topology.

## ACI Integration

A significant architectural decision was to connect the new servers and storage directly to the ACI leaf infrastructure rather than reproducing the legacy connectivity model.

The ACI fabric would then connect upstream using the existing Nexus gateway architecture through a VPC-based trunk design.

This approach positioned ACI as the network fabric for the new datacenter while preserving integration with the existing enterprise network.

## Server and Storage Dependencies

The migration planning included different types of connectivity:

- management interfaces such as iLO/iDRAC;
- server data interfaces;
- storage interfaces;
- iSCSI connectivity;
- network uplinks;
- VLAN/network segments already available in the corporate network.

The planning also considered future storage interfaces that depended on the arrival of new equipment, requiring ports to be identified and reserved in advance.

## Migration Planning Flow

```text
Existing environment inventory
            ↓
Interface and dependency mapping
            ↓
As-Is architecture
            ↓
Capacity / uplink analysis
            ↓
ACI target architecture
            ↓
Server & storage connectivity design
            ↓
Interface reservation
            ↓
Cabling / equipment dependencies
            ↓
To-Be architecture
            ↓
Migration / commissioning
```

## Engineering Considerations

### Dependency mapping

The main risk in a datacenter migration is not necessarily the new technology itself, but an undocumented dependency in the existing environment. Interface and connectivity mapping was therefore an important prerequisite.

### Capacity

The planned expansion from 2 × 10 Gb/s to 4 × 10 Gb/s addressed the need for additional aggregate bandwidth between the network layers.

### ACI adoption

The new environment was designed around Cisco ACI rather than simply extending the legacy switching topology. This changed the connectivity model and required explicit consideration of how the ACI fabric would integrate with existing gateways.

### Physical and logical planning

The migration required both physical planning — ports, links, cabling and equipment — and logical planning — VLANs, trunks, VPC relationships and network dependencies.

## Skills Demonstrated

- Cisco ACI
- Cisco Nexus 5000
- Cisco Nexus 7000
- VPC
- VLAN / trunk connectivity
- 10 Gb/s Ethernet
- Datacenter network architecture
- Server and storage connectivity
- iSCSI
- Network capacity planning
- Datacenter migration planning
- As-Is / To-Be architecture
- Interface inventory and mapping
- Technical documentation

## Outcome / Value

The planning established the technical foundation for moving the JB environment toward a newer ACI-based datacenter architecture while preserving integration with the existing network.

The work also provided a structured inventory of existing connectivity and dependencies, supporting safer migration planning and reducing the risk of overlooking critical server, storage or management connections.

## Confidentiality

This case has been generalized for portfolio purposes. Production IP addresses, serial numbers, hostnames, rack identifiers, exact port assignments and other company-specific operational information have been removed.

The architecture presented here represents the design approach and technical relationships without reproducing the production topology in operational detail.
