---
title: "List MySQL Database"
linkTitle: "db list"
weight: 2
description: >
   List mysql cluster database.
---

#### List Cluster Database

**Usage**:

```shell script
grds mysql db list [flags]
```

**Example:**

List all database on the mysql cluster *my-cluster-test*

```shell
$ grds mysql db list --cluster-name=my-cluster-test
+----------+------+-----------+--------------+
| DATABASE | USER | PRIVILEGE | CHARACTERSET |
+----------+------+-----------+--------------+
|   test   |  -   |     -     |     utf8     |
+----------+------+-----------+--------------+
``````