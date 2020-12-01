---
title: "Grds MySQL List"
linkTitle: "mysql list"
weight: 2
description: >
   List mysql cluster.
---

#### List Cluster

**Usage**:

```shell script
grds mysql list [options] [flags]
```

**Flag**:

| CLI FLAG   | DESCRIPTION                           |
| ---------- | ------------------------------------- |
| --all      | shows all mysql clusters              |
| --selector | selector of the mysql cluster to list |

**Example:**

List all mysql cluster under grds namespace

```shell
$ grds mysql list --all -n grds -w table

> Note: AccessIP is the access entrance of database cluster,firstly use a LoadBalanceIP,if LoadBalanceIP is null,use MasterNodeIP

+-----------------+-----------+---------+-------+-----------+-----------------+-------+
|      NAME       | NAMESPACE | REPLICA | SLAVE |  STATUS   |     ACCESSIP    | PORT  |
+-----------------+-----------+---------+-------+-----------+-----------------+-------+
| my-cluster-test |      grds |       2 |     1 | available |  10.10.120.174  | 30442 |
+-----------------+-----------+---------+-------+-----------+---------+-------+-------+
```
