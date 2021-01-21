---
title: "Create MySQL User"
linkTitle: "user add"
weight: 2
description: >
   Create mysql cluster user.
---

#### Create Cluster User

**Usage**:

```shell script
squidsctl mysql user add <user> <passwd> [flags]
```

**Flag**：

| CLI FLAG | DESCRIPTION                       |
| -------- | --------------------------------- |
| --high   | Create mysql high privilege user. |

**Example:**

Create a user named *bzy* on the mysql cluster *my-cluster-test*

```shell
$ squidsctl mysql user add bzy 123456 --cluster-name=my-cluster-test 
MySQL user created, name: [bzy].
```