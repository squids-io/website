---
title: "Grds Backup List"
linkTitle: "backup list"
weight: 2
description: >
   List backup task.
---

#### List Backup

**Usage**:

```shell script
grds backup list [options] [flags]
```

**Flag**:

| CLI FLAG       | DESCRIPTION                           |
| -------------- | ------------------------------------- |
| --all, -A      | shows all mysql clusters              |
| --selector     | selector of the backup to list        |

**Example:**

List all backup under grds namespace

```shell
$ grds backup list -A -w table
+----------------+-----------+-----------------+----------------------+
|      NAME      | NAMESPACE |   CLUSTERNAME   | STORAGEINTERFACETYPE |
+----------------+-----------+-----------------+----------------------+
| my-backup-test |      grds | my-cluster-test |                  nas |
+----------------+-----------+-----------------+----------------------+

```