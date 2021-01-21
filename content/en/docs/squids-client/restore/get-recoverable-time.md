---
title: "Squids Get Recoverable Time"
linkTitle: "restore get-recoverable-time"
weight: 3
description: >
   Get recoverable time from backup.
---

#### Get CRecoverable Time

**Usage**:

```shell script
squidsctl restore get-recoverable-time <backupName> [flags]
```

**Example:** 

Get recoverable time from backup [my-backup-test]

```shell
squidsctl restore get-recoverable-time my-backup-test -n=squids
Recoverable Time, name: [my-backup-test] time [2020-12-18 14:50:05 ~ 2020-12-18 15:43:36].
```