---
title: "Squids MySQL Delete"
linkTitle: "mysql delete"
weight: 5
description: >
   Delete mysql cluster.
---

#### Delete Cluster

**Usage**:

```shell script
squidsctl mysql delete [options] [flags]
```

**Flag**:

| CLI FLAG   | DESCRIPTION                                        |
| ---------- | -------------------------------------------------- |
| --all      | Delete all clusters under the specified namespace. |
| --selector | The selector to use for delete cluster filtering   |

**Example:**

Delete ==my-cluster-test== cluster under squids namespace

```shell
$ squidsctl mysql-cluster delete my-cluster-test -n squids
MySQL cluster deleted, name: [my-cluster-test] namespace [squids].
```
