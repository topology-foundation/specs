# Topology Protocol

> Definition of CROs and their capabilities

| Lifecycle Stage | Author(s)                 | Latest Revision |
|-----------------|---------------------------|-----------------|
| draft           | [@guiltygyoza](https://github.com/guiltygyoza), [@d-roak](https://github.com/d-roak) | r0, 2024-08-16  |

CURRENTLY WRITING IT

Interest Group:

## Overview

An extended summary of the specification, with all the relevant considerations of the document.

## Introduction

## Methods
Topology Protocol defines a set of interaction methods that indicate the desired action to be performed on a given CRO.

### CREATE
The `CREATE` method declares a new CRO and its corresponding PubSub group.
(one CRO corresponds to one PubSub group for now)

### UPDATE
TBD

### SUBSCRIBE
The `SUBSCRIBE` method subscribes the requester to the given PubSub group.

### UNSUBSCRIBE
The `UNSUBSCRIBE` method unsubscribes the requester from the given PubSub group.

### SYNC
The `SYNC` method reconciles the difference between the local hash graph and the hash graph at the given peer.

## Extensibility
TBD

## Security
Any security consideration that should be taken on the specification or protocol presented.

## References

## Copyright

Copyright and related rights are waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
