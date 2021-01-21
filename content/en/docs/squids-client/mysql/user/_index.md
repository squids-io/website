---
title: "Squids MySQL User Command"
linkTitle: "mysql user"
weight: 7
description: >
   MySQL user management.
---

### MySQL User Management

**Usage**:

```shell script
squidsctl mysql user [command]
```

**Command**：

| COMMAND | DESCRIPTION                        |
| ------- | ---------------------------------- |
| add     | Add a user into the mysql cluster  |
| delete  | Delete user into the mysql cluster |
| list    | List user in the mysql cluster     |
| grant   | List user in the mysql cluster     |
| revoke  | Revoke user privelege for database |

**Flag**：

| CLI FLAG       | DESCRIPTION                                |
| -------------- | ------------------------------------------ |
| --cluster-name | The name of the cluster you want to access |