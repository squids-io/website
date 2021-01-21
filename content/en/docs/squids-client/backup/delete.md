---
title: "Squids Backup Delete"
linkTitle: "backup delete"
weight: 6
description: >
   Delete backup task.
---

**Usage**:

```shell script
squidsctl backup delete [options] [flags]
```

**Flag**:

| CLI FLAG   | DESCRIPTION                                        |
| ---------- | -------------------------------------------------- |
| --all      | Delete all clusters under the specified namespace. |
| --selector | The selector to use for delete cluster filtering   |

**Example:** 

Delete my-cluster-test cluster under squids namespace

```shell
$ squidsctl mysql-cluster delete my-cluster-test -n squids
MySQL cluster deleted, name: [my-cluster-test] namespace [squids].