---
title: "Squids MySQL Show"
linkTitle: "mysql show"
weight: 4
description: >
   Show mysql cluster detail.
---

### Show Cluster

**Usage**:

```shell script
squidsctl mysql show <clusterName> [flags]
```

**Example:**

```shell
$ squidsctl  mysql show my-cluster-test  -w table

> Note: AccessIP is the access entrance of database cluster, firstly use a LoadBalanceIP, if LoadBalanceIP is null, use Master database NodeIP

CLUSTER
+-----------------+-----------+---------+-------+-----------+---------------+-------+
|      NAME       | NAMESPACE | REPLICA | SLAVE |  STATUS   |   ACCESSIP    | PORT  |
+-----------------+-----------+---------+-------+-----------+---------------+-------+
| my-cluster-test |    squids |       2 |     1 | available | 10.10.120.133 | 32324 |
+-----------------+-----------+---------+-------+-----------+---------------+-------+
DATABASE
+----------------------------+-----------+------------+----------+---------------+-------------+---------+---------------+---------------+---------+-----------+
|            NAME            | NAMESPACE | CPUREQUEST | CPULIMIT | MEMORYREQUEST | MEMORYLIMIT | PVCSIZE |    NODEIP     |   NODENAME    |  ROLE   |  STATUS   |
+----------------------------+-----------+------------+----------+---------------+-------------+---------+---------------+---------------+---------+-----------+
| my-cluster-test-replica0-0 |    squids |       500m |        2 |           2Gi |         2Gi |    10Gi | 10.10.120.133 | 10-10-120-133 |  master | available |
| my-cluster-test-replica1-0 |    squids |       500m |        2 |           2Gi |         2Gi |    10Gi | 10.10.120.232 | 10-10-120-232 | standby | available |
|   my-cluster-test-slave0-0 |    squids |       500m |        2 |           2Gi |         2Gi |    10Gi | 10.10.120.174 | 10-10-120-174 |   slave | available |
+----------------------------+-----------+------------+----------+---------------+-------------+---------+---------------+---------------+---------+-----------+
VOLUME
+----------------------------+---------+---------------+-------------------------------------------------------------------------------------------------------+
|            NAME            | PVCSIZE |   NODENAME    |                                                 PATH                                                  |
+----------------------------+---------+---------------+-------------------------------------------------------------------------------------------------------+
| my-cluster-test-replica0-0 |    10Gi | 10-10-120-133 | /var/lib/k3s/local-path/pvc-0a1f85b5-7bd8-4ce6-93dd-7653350b5159_squids_data-my-cluster-test-replica0-0 |
| my-cluster-test-replica1-0 |    10Gi | 10-10-120-232 | /var/lib/k3s/local-path/pvc-d3928c72-49bb-4c9e-aa45-bfa3ff0cae3c_squids_data-my-cluster-test-replica1-0 |
|   my-cluster-test-slave0-0 |    10Gi | 10-10-120-174 |   /var/lib/k3s/local-path/pvc-a1657f5d-c722-4315-97f1-b95838b1e85c_squids_data-my-cluster-test-slave0-0 |
+----------------------------+---------+---------------+-------------------------------------------------------------------------------------------------------+
```

