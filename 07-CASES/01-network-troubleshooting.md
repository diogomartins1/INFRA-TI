# Case 01 — Network Troubleshooting

## Objective

Demonstrate a structured approach to diagnosing connectivity problems in enterprise network environments.

## Context

Enterprise infrastructure depends on multiple interconnected layers: endpoints, VLANs, switching, routing, security controls, physical links and upstream services. A connectivity symptom does not necessarily indicate a failure in the component where the problem is first observed.

## Problem

A service or endpoint becomes intermittently or completely unreachable, requiring investigation across the network path.

## Investigation approach

### 1. Define the symptom

- What source and destination are affected?
- Is the failure total or intermittent?
- Does it affect one host, one VLAN, one site or multiple locations?
- When did the behavior begin?
- Was there a recent change?

### 2. Establish the network path

Validate the expected path through:

- endpoint and gateway
- VLAN and switching layer
- routing table
- next-hop reachability
- firewall/security controls
- destination service

### 3. Collect evidence

Useful evidence includes:

- interface status and counters
- VLAN membership
- MAC address tables
- ARP information
- routing tables
- BGP/OSPF state where applicable
- packet loss and latency
- firewall session and policy logs
- monitoring history
- recent configuration changes

### 4. Form hypotheses

Typical hypotheses include:

- physical or logical link failure
- incorrect VLAN configuration
- routing inconsistency
- asymmetric path
- interface errors or packet loss
- firewall policy blocking traffic
- DNS/service-layer issue
- recent configuration change

### 5. Isolate the fault domain

The objective is to reduce the problem from a broad connectivity symptom to a specific layer, path or component.

## Root Cause

The root cause should only be declared after the evidence supports the hypothesis. A symptom such as “host cannot connect” is not itself a root cause.

## Resolution

Apply the minimum corrective action required to restore service, while considering change control, availability and rollback.

## Validation

After correction:

- reproduce the original test
- validate end-to-end connectivity
- check interfaces and logs
- confirm that related services remain healthy
- monitor for recurrence

## Prevention

Where appropriate, document:

- root cause
- corrective action
- configuration or process improvement
- monitoring opportunity
- operational documentation update

## Technical takeaway

Effective infrastructure troubleshooting is not a sequence of commands. It is a process of hypothesis formation, evidence collection, fault isolation, root-cause analysis and controlled validation.

## Confidentiality

This case is intentionally generalized and does not expose company-specific topology, IP addresses, device identifiers, configurations or operational data.
