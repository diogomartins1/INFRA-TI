# Case 05 — PAM/MAM Proof of Concept on Google Cloud

## Context

Proof of Concept (PoC) for evaluating the deployment of components of a **PAM/MAM media-management ecosystem** in Google Cloud, integrated with an existing on-premises environment.

The initiative required adapting the cloud environment to application requirements that were still aligned with a traditional bare-metal/server deployment model.

## Architecture

The PoC architecture connected a Google Cloud VPC to the on-premises environment through **Cloud Interconnect**. The cloud side hosted application instances, while the on-premises environment retained the existing media infrastructure and shared storage platform.

The reference architecture included:

- Google Cloud VPC;
- Compute instances for application components;
- Cloud Interconnect connectivity;
- on-premises media infrastructure;
- enterprise media storage;
- hybrid communication between cloud and on-premises components.

## Technical Challenge

The application vendor's cloud readiness did not yet match the organization's standard cloud provisioning model. The PoC therefore required infrastructure adaptations before the application could be evaluated in the target environment.

A particularly relevant constraint was the operating system. The vendor required a **CentOS** distribution compatible with the application, while CentOS was no longer part of the organization's standard catalog of approved **golden images**.

The standard image catalog incorporated requirements from security, infrastructure, monitoring and compliance teams, including preconfigured operational automations. Using an unsupported image would therefore require an explicit exception for the PoC.

## My Role

As an Infrastructure/DevOps/Networks analyst, I was responsible for the infrastructure side of the PoC, working with the vendor's technical representatives to make the cloud environment compatible with the application requirements.

My activities included:

- provisioning and configuring the required Google Cloud instances;
- adapting the cloud infrastructure to the application's technical requirements;
- aligning the implementation with the vendor's technical team;
- coordinating the exception required for the non-standard CentOS image;
- reproducing the required disk/partition layout based on the existing bare-metal model;
- enabling the corresponding cloud resources and configurations;
- supporting the hybrid architecture between Google Cloud and the on-premises environment.

## Golden Image Exception

The use of CentOS required an exception to the organization's normal provisioning standard.

The decision was not simply to deploy an arbitrary operating-system image. The PoC required coordination between the application vendor and internal infrastructure, security, monitoring and compliance requirements so that the exception could be controlled within the scope of the evaluation.

This provided an important practical lesson: **cloud adoption is not always a matter of creating a VM and installing an application. Existing standards, vendor requirements, security controls and operational models can become architectural dependencies.**

## Disk and Partitioning Requirements

Another challenge was that the application expected a storage layout consistent with its traditional bare-metal deployment.

The cloud instances therefore had to reproduce the required partitioning model rather than simply using the default disk configuration offered by the cloud platform.

This required translating a physical-server requirement into a cloud infrastructure implementation while preserving the application's expected storage structure.

## Implementation Flow

```text
Application requirements
        ↓
Vendor technical alignment
        ↓
Cloud infrastructure requirements
        ↓
Golden Image compatibility analysis
        ↓
Controlled CentOS exception
        ↓
GCP instance provisioning
        ↓
Required disk / partition layout
        ↓
Cloud resource configuration
        ↓
Hybrid connectivity
        ↓
PoC environment available for application testing
```

## Key Technical Decisions

### 1. Adapt the infrastructure instead of changing the application prematurely

The objective of the PoC was to evaluate the application under realistic conditions. Infrastructure was therefore adapted to satisfy the vendor's documented requirements within the controlled scope of the PoC.

### 2. Treat the operating system as an organizational dependency

The CentOS requirement affected more than the VM configuration. It intersected with image governance, security, monitoring and compliance standards.

### 3. Preserve application assumptions during cloud migration

The required disk and partition structure demonstrated that applications designed around physical or traditional infrastructure can carry assumptions that must be explicitly addressed during cloud adoption.

### 4. Work directly with the vendor

The implementation depended on close technical alignment with the vendor's representative team. This reduced ambiguity around application prerequisites and allowed infrastructure decisions to be validated against the actual product requirements.

## Skills Demonstrated

- Google Cloud infrastructure
- VPC and hybrid connectivity concepts
- Compute instance provisioning
- Cloud Interconnect
- Linux infrastructure
- CentOS
- Disk and filesystem planning
- Bare-metal to cloud adaptation
- Infrastructure standards and golden images
- Security/compliance constraints
- Vendor technical coordination
- PoC infrastructure design and implementation

## Lessons Learned

This PoC reinforced that infrastructure engineering in enterprise environments involves balancing three dimensions:

1. **Technical requirements** — what the application needs to operate;
2. **Organizational standards** — what infrastructure, security, monitoring and compliance teams allow;
3. **Delivery objectives** — what must be made available to validate the solution within the PoC scope.

The role of infrastructure was therefore not merely to provision cloud resources, but to translate application requirements into an environment that could operate within enterprise constraints.

## Confidentiality

This case is intentionally generalized. Company names, people, internal hostnames, IP addresses, detailed configurations, proprietary architecture information and operational identifiers have been omitted.

The architecture diagram is presented as a high-level representation of the PoC and does not expose confidential configuration details.
