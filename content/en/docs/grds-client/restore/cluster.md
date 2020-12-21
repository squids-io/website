---
title: "Grds Restore Cluster"
linkTitle: "restore cluster"
weight: 2
description: >
   Restore a cluster.
---

#### Restore Cluster

**Usage**:

```shell script
grds restore cluster <restoreClusterName> [flags]
```

**Flag**：

| CLI FLAG        | DESCRIPTION                                                  |
| --------------- | ------------------------------------------------------------ |
| --cpu           | Set the number of millicores to request for the CPU, e.g. "100m" or "0.1" |
| --cpu-limit     | Set the number of millicores to limit for the CPU, e.g. "100m" or "0.1" |
| --labels        | The labels to apply to this cluster                          |
| --memory        | Set the amount of RAM to request, e.g. 1GiB. Overrides the default server value |
| --memory-limit  | Set the amount of RAM to limit, e.g. 1GiB.                   |
| --pvc-size      | The size of the PVC capacity for Database instances. Must follow the standard Kubernetes format, e.g. "10.1Gi" (default "10Gi") |
| --backup-name   | The backup name that you want to restore.|
| --restore-method  | The restore method that you want to restore, e.g. PointInTime/BackupSet. |
| --backup-set-id | If use BackupSet method, Specify a backup set that you need to restore. |
| --point-in-time | If use PointInTime method, Specify a time point that you need to restore. |

**Example:** 

Restore a cluster named restore-cluster use BackupSet method from backup [my-backup-test]

```shell
grds restore cluster restore-cluster --backup-name=my-backup-test --restore-method=BackupSet --backup-set-id=my-backup-test-full-gl22d-1608274200 --cpu=0.5 --cpu-limit=2 --memory=2Gi --memory-limit=2Gi --pvc-size=21Gi -n=grds
Cluster restored, name: [restore-cluster] namespace [default] type [mysql].
```