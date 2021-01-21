---
title: "Authorize the database to the user"
linkTitle: "user grant"
weight: 3
description: >
   Assigns privileges of database to MySQL user accounts.
---

### Authorize the database to the user

**Usage**:

```shell script
squidsctl mysql user grant <user> <database> <ro/rw> [flags]
```

**Example:** 

Grant users *bzy* to read and write the database *test*

```shell
$ squidsctl mysql user grant bzy test rw --cluster-name=my-cluster-test
MySQL user granted, user [bzy] database[test] privilege [rw].
$ squidsctl mysql user list --cluster-name=my-cluster-test
+------+----------+-----------+-----------+
| USER | DATABASE | PRIVILEGE | HIGH-PRIV |
+------+----------+-----------+-----------+
| bzy  |   test   |    rw     |   false   |
+------+----------+-----------+-----------+
```