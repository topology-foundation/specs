# Conflict-free Replicated Objects

> Definition of CROs and their capabilities

| Lifecycle Stage | Author(s)                 | Latest Revision |
|-----------------|---------------------------|-----------------|
| draft           | [@guiltygyoza](https://github.com/guiltygyoza), [@d-roak](https://github.com/d-roak) | r0, 2024-05-24  |

CURRENTLY WRITING IT

Interest Group: [@0xMugen](https://github.com/0xMugen)

## Overview
Conflict-free Replicated Object (CRO) is the primary abstraction of the Topology Protocol. This document specifies CRO's internal structure, interaction methods, and considerations in extensibility and security.

## Introduction
Conflict-free Replicated Object (CRO) is the core abstraction of the Topology Protocol, designed to enable real-time, multi-user, interoperable, and censorship-resistant applications on open decentralized networks. CROs are composable programmable objects that can be updated concurrently in real-time and subscribed to as publish/subscribe (PubSub) groups on open peer-to-peer (P2P) networks.

The protocol defines the basic structure that every CRO must follow. The protocol also defines a set of methods for interacting with any CRO.

## Structure
The basic structure of every CRO consists of the following components: state, interface, signal handlers, merge function, and additional functions.

**Q1: is hash graph opt-in or forced? for example, a CRO whose state is just a GSet doesn't need hash graph because ordering doesn't matter for it.**

### State
States are typed by either built-in CRDTs provided by the protocol, or by other CROs.

### Interface
The interface specifies the set of signals recognized by the CRO, as well as the set of functions that can be invoked at any replica of the CRO.

### Signal handlers
Signal handlers turn signals into operations applied on the state.

### Merge function
The merge function specifies how the state coming from a peer replica is merged with the local state. This function must be commutative, associative, and idempotent: denote the merge operation as $\cup$, then $A \cup B = B \cup A$, $A \cup (B \cup C) = (A \cup B) \cup C$, and $A \cup A = A$.

### Additional functions
CRO may have additional functions, invocable by any replica locally. Some functions may be accessors that materialize the state into values, dropping tombstones and metadata. Other functions may apply operations on the state.

## Methods
Topology Protocol defines a set of interaction methods that indicate the desired action to be performed on a given CRO.

### CREATE
The `CREATE` method declares a new CRO and its corresponding PubSub group.

**Note: assuming one CRO corresponds to one PubSub group**

### UPDATE
TBD; The `UPDATE` method ...

**Q3: what is the relationship between `UPDATE` and CRO signal? also, for a signal that is sent to a CRO replica, is the signal wrapped in a message and gossiped through the subscriber subnet?**

### SUBSCRIBE
The `SUBSCRIBE` method subscribes the requester to the given PubSub group.

### UNSUBSCRIBE
The `UNSUBSCRIBE` method unsubscribes the requester from the given PubSub group.

### SYNC
The `SYNC` method reconciles the difference between the local CRO state and the CRO state at the given peer.

**Q4: reconciling state? or hash graph? related to Q1**

## Extensibility
TBD

## Security
Any security consideration that should be taken on the specification or protocol presented.

## References

## Copyright
Copyright and related rights are waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
