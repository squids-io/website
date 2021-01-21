---
title: "Delete MySQL User"
linkTitle: "user delete"
weight: 5
description: >
   Delete mysql cluster user.
---

#### Delete Cluster User

**Usage**:

```shell script
squidsctl mysql user delete [options] [flags]
```

**Example:** 

Delete a database named *test* on the mysql cluster *my-cluster-test*

```shell
$ squidsctl  mysql user delete bzy --cluster-name=my-cluster-test
MySQL user deleted, name: [bzy].
```