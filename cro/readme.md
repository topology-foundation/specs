# Conflict-free Replicated Objects

> Definition of CROs and their capabilities

| Lifecycle Stage | Author(s)                 | Latest Revision |
|-----------------|---------------------------|-----------------|
| draft           | [@guiltygyoza](https://github.com/guiltygyoza), [@d-roak](https://github.com/d-roak) | r0, 2024-05-24  |

CURRENTLY WRITING IT

Interest Group: [@0xMugen](https://github.com/0xMugen)

## Overview
Conflict-free Replicated Object (CRO) is the primary abstraction of the Topology Protocol. This document specifies CRO's internal structure and their 5 basic capabilities.

## Introduction
CROs are programmable objects that are replicated, updateable by multiple writers concurrently and in a coordination-free manner. The design purpose of CROs is to provide a simple, lightweight, and flexible abstraction for constructing peer-to-peer multiplayer applications.

The key properties of CROs are provided by conflict-free replicated data types (CRDTs). CROs are composable by way of CRDT's composability, making every CRO effectively a compound CRDT.

## Structure
Every CRO consists of the following components: states, mutators, accessors, and a merge function.

States are typed either by CRDTs or by other CROs. Topology Protocol specifies a set of built-in CRDTs that are correct, which serve as the building blocks for CROs.

Mutators are functions that modify the states. Mutators must be monotonic: they must never destroy information from states, only inflate them. Monotonicity is the basis for coordination-free state consistency [Hellerstein & Alvaro 2019].

Accessors are read-only functions that materialize the states into values.

The merge function specifies how the states of two replicas of the same CRO are merged into a single set of states. This function must be commutative.

## Extensibility
TBD

## Capabilities and Messages
Intro TBD; Things to clarify

- we need clarity on the relationship between pubsub group topic and object ID, specifically is there's a level of indirection between them i.e. if topic maps to object ID one to one or if the mapping is one to many.

- Q: A new peer wishes to "join" object X. Examine this scenario: the peer synchronizes on X first, then upon finishing the sync, the peer subscribes to X. Assume synchronization means synchronizing on the history of an object at the moment of sync request. Also, assume subscription means receiving all updates to the object *after* the subscription is activated. I am worried that there can be "gaps" in the causal history of updates between the moment of synchronization and the moment of subscribe.

### CREATE
TBD; blueprints

### UPDATE
`updateObject (local object replica, update data)`

### SUBSCRIBE
`subscribeObjectByID (object ID)`

### UNSUBSCRIBE
`unsubscribeObjectByID (object ID)`

### SYNCHRONISE
TBD; `synchronizeObjectByID (object ID)` which connects to a random peer currently subscribing to the object ID and synchronizes with it?

## Security

Any security consideration that should be taken on the specification or protocol presented.

## References

[Hellerstein & Alvaro 2019] https://arxiv.org/pdf/1901.01930

## Copyright

Copyright and related rights are waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
