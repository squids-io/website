---
title: "Deploy MySQL Operator from Kubernetes Manifests"
linkTitle: "Manifest"
weight: 20
date: 2020-11-25
description: >
  Install mysql operator by manifests
---

## Deploy MySQL operator from Kubernetes Manifests


1. Create a Namespace called "squids".

    ```bash
    kubectl create ns squids
    ```

2. Create a ServiceAccount and install cluster roles.

    ```bash
    kubectl -n squids create -f https://raw.githubusercontent.com/squids-io/grds/{{< param operatorVersion >}}/installers/manifests/rbac.yaml
    ```

3. Apply the CRD.

    ```bash
    kubectl -n squids create -f https://raw.githubusercontent.com/squids-io/grds/{{< param operatorVersion >}}/installers/manifests/mysql.squids.io_mysqlclusters.yaml
    ```

4. Deploy the MySQL operator.

    ```bash
   kubectl -n squids create -f https://raw.githubusercontent.com/squids-io/grds/{{< param operatorVersion >}}/installers/manifests/deployment.yaml
    ```

### Check the MySQL operator deployment

To verify that the installation was successful, complete the following steps.

1. Check the status of the pods. You should see a new mysql-operator pod

    ```bash
    $ kubectl get pods -n squids
    NAME                                        READY   STATUS    RESTARTS   AGE
    mysql-operator-76c44cdc5c-lw4z6             1/1     Running   0          53s
    ```

2. Check the CRDs. You should see the following MySQL cluster CRDs.
mysql-cluster-crd.png

    ```bash
    $ kubectl get crd | grep squids
    NAME                                    CREATED AT
    mysqlclusters.mysql.squids.io          2020-10-28T09:53:01Z
    ```
