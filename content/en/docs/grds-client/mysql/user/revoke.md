---
title: "Revoke User Privileges"
linkTitle: "user revoke"
weight: 4
description: >
   Revoke user privileges of database
---

#### Revoke User Privileges

**Usage**:

```shell script
grds mysql user revoke <user> <database> [flags]
```

**Example:** 

Revoke users *bzy* to read and write the database *test*

```shell
$ grds  mysql user revoke bzy test --cluster-name=my-cluster-test
MySQL user revoked, user [bzy] database[test]
$ grds mysql user list --cluster-name=my-cluster-test
+------+----------+-----------+-----------+
| USER | DATABASE | PRIVILEGE | HIGH-PRIV |
+------+----------+-----------+-----------+
| bzy  |    -     |     -     |   false   |
+------+----------+-----------+-----------+
```