---
title: "Squids Backup Full Backup Manually"
linkTitle: "backup manual-full-job"
weight: 3
description: >
   Create full backup job manually.
---

#### Create A Full Backup Job Manually

**Usage**:

```shell script
squidsctl backup manual-full-job <backupName> [options] [flags]
```

**Flag**:

| CLI FLAG           | DESCRIPTION                                                   |
| ------------------ | ------------------------------------------------------------- |
| --backup-name      | The backup name that you want to create backup job manually.  |

**Example:** 

Create a full backup job manually for my-cluster-test under squids namespace

```shell
$ squidsctl backup manual-full-job --backup-name=my-backup-test
Manual backup Job created, name: [my-backup-test-full--test-1606909374] namespace [squids].
```