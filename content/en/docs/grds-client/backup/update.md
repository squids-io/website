---
title: "Grds Backup Update"
linkTitle: "backup update"
weight: 5
description: >
   Update backup task.
---

#### Update Backup

**Usage**:

```shell script
grds backup update <backupName> [options] [flags]
```

**Flag**:

| CLI FLAG                             | DESCRIPTION                                                 |
| ------------------------------------ | ----------------------------------------------------------- |
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

Update a backup's full backup schedule that named my-backup-test

```shell
$ grds backup update my-backup-test --full-backup-schedule="0 1 * * *"
Backup updated, name: [my-backup-test] namespace [grds].
```