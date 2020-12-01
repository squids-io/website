---
title: "Grds MySQL Update"
linkTitle: "mysql update"
weight: 3
description: >
   Update mysql update.
---

#### Update Cluster

**Usage**:

```shell script
grds mysql update <clusterName> [flags]
```

**Flag**:

| CLI FLAG        | DESCRIPTION                                                  |
| --------------- | :----------------------------------------------------------- |
| --cpu           | Set the number of millicores to request for the CPU, e.g. "100m" or "0.1" |
| --cpu-limit     | Set the number of millicores to limit for the CPU, e.g. "100m" or "0.1" |
| --memory        | Set the amount of RAM to request, e.g. 1GiB. Overrides the default server value |
| --memory-limit  | Set the amount of RAM to limit, e.g. 1GiB.                   |
| --pvc-size      | The size of the PVC capacity for Database instances. Must follow the standard Kubernetes format, e.g. "10.1Gi" |
| --replica-count | The number of primary candidate to create as part of the cluster. |
| --slave-count   | The number of slave to create as part of the cluster         |



**Example:**

Online add a slave to mysql-cluster-test cluster under grds namespace

```shell
$ grds mysql update my-cluster-test --slave-count=2
MySQL cluster updated, name: [my-cluster-test] namespace [grds].
$
$ grds mysql list -n grds -w table
+-----------------+-----------+---------+-------+
|      NAME       | NAMESPACE | REPLICA | SLAVE |
+-----------------+-----------+---------+-------+
| my-cluster-test |      grds |       2 |     2 |
+-----------------+-----------+---------+-------+
$
```
Change the CPU limit of the whole my-cluster-test cluster
> ==Note: when you change CPU/memory option,operator will restart the whole MySQL cluster to adjust to the new config!==

```shell
$ grds mysql update my-cluster-test --cpu-limit=4
MySQL cluster updated, name: [my-cluster-test] namespace [grds].
$
$ grds mysql show my-cluster-test -w table
+--------------------+-----------+------------+----------+---------------+-------------+---------+---------------+---------------+---------+-----------+
|        NAME        | NAMESPACE | CPUREQUEST | CPULIMIT | MEMORYREQUEST | MEMORYLIMIT | PVCSIZE |    NODEIP     |   NODENAME    |  ROLE   |  STATUS   |
+--------------------+-----------+------------+----------+---------------+-------------+---------+---------------+---------------+---------+-----------+
| my-test-replica0-0 |      grds |          0 |        4 |             0 |           0 |    10Gi | 10.10.120.174 | 10-10-120-174 |  master | available |
| my-test-replica1-0 |      grds |          0 |        4 |             0 |           0 |    10Gi | 10.10.120.232 | 10-10-120-232 | standby | available |
+--------------------+-----------+------------+----------+---------------+-------------+---------+---------------+---------------+---------+-----------+
$
```

