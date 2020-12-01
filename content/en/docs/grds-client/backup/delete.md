---
title: "Grds Backup Delete"
linkTitle: "backup delete"
weight: 5
description: >
   Delete backup task.
---

**Usage**:

```shell script
grds backup delete [options] [flags]
```

**Flag**:

| CLI FLAG   | DESCRIPTION                                        |
| ---------- | -------------------------------------------------- |
| --all      | Delete all clusters under the specified namespace. |
| --selector | The selector to use for delete cluster filtering   |

**Example:** 

Delete my-cluster-test cluster under grds namespace

```shell
$ grds mysql-cluster delete my-cluster-test -n grds
MySQL cluster deleted, name: [my-cluster-test] namespace [grds].