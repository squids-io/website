---
title: "Delete MySQL Database"
linkTitle: "db delete"
weight: 5
description: >
   Delete mysql cluster Database.
---

#### Delete Cluster Database

**Usage**:

```shell script
grds mysql db delete [options] [flags]
```

**Example:** 

Delete a database named *test* on the mysql cluster *my-cluster-test*

```shell
$ grds mysql db delete test --cluster-name=my-cluster-test
MySQL schema deleted, name: [test].
```