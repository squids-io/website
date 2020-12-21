---
title: "List MySQL User"
linkTitle: "user list"
weight: 2
description: >
   List mysql cluster user.
---

#### List Cluster User

**Usage**:

```shell script
grds mysql user list [flags]
```

**Example:**

List all user on the mysql cluster *my-cluster-test*

```shell
$ grds mysql user list --cluster-name=my-cluster-test
+------+----------+-----------+-----------+
| USER | DATABASE | PRIVILEGE | HIGH-PRIV |
+------+----------+-----------+-----------+
| bzy  |    -     |     -     |   false   |
+------+----------+-----------+-----------+
```