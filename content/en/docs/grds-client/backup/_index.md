---
title: "Grds Backup Command"
linkTitle: "Backup Command"
weight: 1
description: >
   The lifecycle of managed backup.
---

### Backup Lifecycle Management

**Usage**:

```shell script
grds backup [command]
```

**Command**：

| COMMAND | DESCRIPTION                                 |
| ------- | ------------------------------------------- |
| create  | Create a backup into the k8s cluster    |
| manual-full-job  | Create a full backup job manually    |
| delete  | Delete a backup from the k8s cluster |
| list    | List backup in the cluster           |
| Update  | Update a backup in the k8s cluster   |