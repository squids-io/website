---
title: "Prerequisites"
linkTitle: "Prerequisites"
weight: 10
date: 2020-11-25
description: >
    The following is required prior to installing MySQL Operator
---

The following is required prior to installing MySQL Operator.

## Environment

The MySQL Operator is tested in the following environments:

* Kubernetes v1.14.x or k3s
* Amazon EKS

## Client Interfaces

The MySQL Operator installer will install the [`squids` client]({{< relref "docs/squids-client" >}}) interface
to help with using the MySQL Operator. However, it is also recommend that
you have access to [`kubectl`](https://kubernetes.io/docs/tasks/tools/install-kubectl/) and are able to communicate with the
Kubernetes cluster that you are working with.

## Ports

There are several application ports to note when using the MySQL Operator.
These ports allow for the [`squids` client]({{< relref "docs/squids-client" >}})
to interface with the MySQL Operator API:

| Container | Port |
| --- | --- |
| API Server | 8443 |