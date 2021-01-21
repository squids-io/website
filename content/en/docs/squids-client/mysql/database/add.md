---
title: "Create MySQL Database"
linkTitle: "db add"
weight: 2
description: >
   Create mysql cluster database.
---

#### Create Cluster Database

**Usage**:

```shell script
squidsctl mysql db add <user> [flags]
```

**Flag**：

| CLI FLAG        | DESCRIPTION                                        |
| --------------- | -------------------------------------------------- |
| --character-set | Set the character set of database (default "utf8") |

**Example:**

Create a database named *test* on the mysql cluster *my-cluster-test*

```shell
$ squidsctl mysql db add test --character-set=utf8 --cluster-name=my-cluster-test
MySQL schema created, name: [test] characterSet [utf8].
```
