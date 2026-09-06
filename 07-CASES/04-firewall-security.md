# Case 04 — Firewall, Virtualization & Application Resilience

## Context

During an earlier infrastructure engagement, I worked on initiatives involving network security, virtualization, monitoring and application availability.

The environment had constraints around physical-server investment while development teams needed greater agility to provision environments for new solutions. At the same time, the main user-facing application database experienced instability during periods of high simultaneous demand.

## My Role

My activities covered infrastructure implementation and configuration, including:

- firewall rule configuration with `iptables`;
- Proof of Concept (PoC) with pfSense for a branch office;
- implementation of VMware ESXi as a virtualization platform;
- creation of separate development/homologation and production environments;
- network segmentation between environments;
- replacement of the existing monitoring solution with Zabbix;
- analysis of application/database behavior during peak demand;
- implementation of a load-balancing strategy using Nginx and virtual machines in production.

## Firewall & Network Security

### iptables

I worked directly with `iptables`, configuring firewall rules according to the connectivity requirements of the environment.

The work involved translating required communications into appropriate network access rules while preserving segmentation and access control.

### pfSense PoC

I also conducted a Proof of Concept with **pfSense** for a branch office.

The objective was to evaluate an alternative firewall/network-security platform for the branch environment and validate its applicability before a broader implementation.

The PoC provided practical experience with firewall concepts, rule configuration and the relationship between network requirements and security controls.

## Virtualization with VMware ESXi

A major infrastructure constraint was the limited availability of investment for new physical servers, combined with the need for development teams to provision virtual machines for new solutions.

I implemented **VMware ESXi** as an alternative to continuously acquiring physical servers.

The resulting model provided separate environments for:

```text
                    VMware ESXi
                         │
             ┌───────────┴───────────┐
             │                       │
      Development /              Production
       Homologation
             │                       │
       Network Segment A       Network Segment B
```

The environments were intentionally segmented, allowing development and homologation workloads to be isolated from production workloads.

This approach increased infrastructure flexibility while addressing the immediate constraint on physical-server acquisition.

## Monitoring Modernization

The existing monitoring solution was replaced by **Zabbix**.

The objective was to establish a more suitable monitoring platform for the infrastructure and improve visibility into the health and behavior of the environment.

The work involved implementing the monitoring platform and adapting monitoring to the infrastructure components that needed operational visibility.

## Application Availability During Peak Demand

One of the most relevant challenges involved the database supporting the organization's main user-facing application.

During peak periods, such as days with high volumes of boleto payments, the number of simultaneous requests could cause the database to become unavailable.

The approach was to reduce the concentration of application requests on a single production instance by introducing additional virtual machines and placing **Nginx** in front of them as a load balancer using a **round-robin** strategy.

The simplified architecture was:

```text
                  Users
                    │
                    ▼
                 Nginx
              Load Balancer
                    │
          ┌─────────┼─────────┐
          ▼         ▼         ▼
        VM-01     VM-02     VM-03
          │         │         │
          └─────────┼─────────┘
                    ▼
              Application / DB
```

The strategy allowed additional production virtual machines to be made available during periods of higher demand and distributed incoming requests across the available instances.

## Implementation Logic

The overall infrastructure approach connected several initiatives:

```text
Limited physical-server investment
              ↓
       VMware ESXi
              ↓
 Multiple virtual machines
              ↓
 ┌────────────┴────────────┐
 │                         │
Dev / Homologation       Production
 │                         │
 └──────── Network segmentation
                           │
                           ▼
                    Nginx Load Balancer
                           │
                    Multiple VMs
                           │
                           ▼
                 Application availability
```

Security and monitoring were complementary components of the environment:

```text
Firewall / Access Control → Segmentation → Virtual Infrastructure
                                      ↓
                                  Monitoring
                                   (Zabbix)
```

## Technical Decisions

### Virtualization as an infrastructure strategy

Rather than treating virtualization only as a technology change, VMware ESXi was used to address a concrete infrastructure constraint: the need to provision additional environments without proportional investment in physical servers.

### Environment separation

Development/homologation and production were kept in separate network segments to reduce the risk of interference between workloads and provide a clearer operational boundary.

### Capacity during predictable peaks

The application availability problem was associated with predictable periods of high demand. The response was therefore designed around the ability to provision additional production VMs and distribute incoming traffic through Nginx.

### Monitoring as an operational foundation

Replacing the previous monitoring platform with Zabbix provided a more appropriate foundation for observing the infrastructure and supporting operational visibility.

## Skills Demonstrated

- Linux / iptables
- pfSense
- VMware ESXi
- Virtualization
- Network segmentation
- Firewall rules and access control
- Zabbix
- Nginx
- Load balancing / round-robin
- Infrastructure capacity planning
- Application availability
- Production and homologation environments
- Infrastructure PoCs

## Key Lessons

This experience reinforced an important infrastructure principle: **technical solutions should address the operational constraint, not simply introduce a technology.**

In this environment, virtualization addressed physical-server constraints, network segmentation established boundaries between environments, monitoring improved operational visibility, and load balancing provided a practical strategy for handling predictable application demand.

## Confidentiality

This case is intentionally generalized. Company names, people, internal hostnames, IP addresses, detailed firewall rules, application/database names, credentials, topology details and other proprietary information have been omitted.

The architecture shown is conceptual and does not reproduce the original production configuration.
