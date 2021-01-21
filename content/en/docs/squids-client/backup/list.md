---
title: "Squids Backup List"
linkTitle: "backup list"
weight: 4
description: >
   List backup task.
---

#### List Backup

**Usage**:

```shell script
squidsctl backup list [options] [flags]
```

**Flag**:

| CLI FLAG       | DESCRIPTION                           |
| -------------- | ------------------------------------- |
| --all, -A      | shows all mysql clusters              |
| --selector     | selector of the backup to list        |

**Example:**

List all backup under squids namespace

```shell
$ squidsctl backup list -A -w table
+----------------+-----------+-----------------+----------------------+
|      NAME      | NAMESPACE |   CLUSTERNAME   | STORAGEINTERFACETYPE |
+----------------+-----------+-----------------+----------------------+
| my-backup-test |    squids | my-cluster-test |                  nas |
+----------------+-----------+-----------------+----------------------+

```