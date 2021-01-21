---
title: "Squids MySQL Database Command"
linkTitle: "mysql db"
weight: 6
description: >
   MySQL Database management.
---

### MySQL Database Management

**Usage**:

```shell script
squidsctl mysql db [command]
```

**Command**：

| COMMAND | DESCRIPTION                            |
| ------- | -------------------------------------- |
| add     | Add a database into the mysql cluster  |
| delete  | Delete database into the mysql cluster |
| list    | List database in the mysql cluster     |

**Flag**：

| CLI FLAG       | DESCRIPTION                                |
| -------------- | ------------------------------------------ |
| --cluster-name | The name of the cluster you want to access |