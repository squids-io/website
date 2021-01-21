---
title: "Squids Backup Create"
linkTitle: "backup create"
weight: 2
description: >
   Create backup task.
---

#### Create Backup

**Usage**:

```shell script
squidsctl backup create <backupName> [options] [flags]
```

**Flag**：

| CLI FLAG        | DESCRIPTION                                                  |
| --------------- | ------------------------------------------------------------ |
| --cluster-name  | the cluster name that need to backup |
| --db-type       | the cluster's db type(mysql, mssql) (default mysql) |
| --full-backup-schedule        | the cron expression of backup to take a full backup schedule. (default "0 0 * * *") |
| --incremental-backup-schedule       | the cron expression of backup to take an incremental backup schedule. (default "0 6,12,18   *   *   *") |
| --clean-backup-schedule       | the cron expression of backup to take a clean backup schedule. (default "0 21   *   *   *") |
| --retention-policy       | retention policy of current backup set, e.g. FullBackupSetNumber/ExpireDuration. (default "FullBackupSetNumber") |
| --full-backup-set-retention-number       | number of reserved full backup sets. (default 10) |
| --backup-set-expire-duration       | the expiration time of the backup set. (default "7d") |
| --storage-interface-type       |  the storage interface type for store backup set, e.g. nas/s3. (default "nas") |
| --nas-protocol       | the protocol for store backup set. (default "nfs") |
| --nfs-name       |  the name of storage interface. |
| --nfs-backup-path       | the nfs backup path for store backup set. |
| --nfs-address       | the nfs host ip. |
| --nfs-port       | the nfs storage interface port. (default 2049) |
| --nfs-username       | the nfs username. |
| --nfs-password       | the nfs password. |
| --aws-access-key-id       |  the aws s3 access key id. |
| --aws-secret-access-key       | the aws s3 secret access key. |
| --aws-endpoint       | the aws s3 endpoint. |

**Example:**

Create a backup task ==my-backup-test== for ==my-cluster-test== in the squids namespace,
the task will run under the default backup schedule 

```shell
$ squidsctl backup create my-backup-test --cluster-name=my-cluster-test --db-type=mysql \
    --storage-interface-type=nas --nas-protocol=nfs --nfs-name=mynfs --nfs-address=10.10.120.201 \
    --nfs-backup-path=/backup/data/nfs --nfs-port=2049 
Backup created success, name: [my-backup-test] namespace [squids].
```

Create a full backup task ==fullbackup-task== for ==my-cluster-test== in the squids namespace

```shell
==need command!!!==
```

Create a incremental backup task ==incremental-task== for ==my-cluster-test== in the squids namespace

```shell
==need command!!!==
```
