---
title: "Install grds CLI"
linkTitle: "Grds CLI"
weight: 50
date: 2020-11-25
description: >
  Install grds CLI
---

`grds` cli is a command tool for k8s database operator management,we recommend using `grds` to manage database operator in terminal console.
After database operator deployment,you can run following command to install `grds`:

```shell
curl https://raw.githubusercontent.com/GrdsCloud/grds/{{< param operatorVersion >}}/installers/kubectl/client-setup.sh > client-setup.sh
chmod +x client-setup.sh
./client-setup.sh
```
It will prompt for some environment variables,you should add these environment variables to bash profile:

```
cat <<EOF >> ~/.bash_profile
export GRDS_CA_CERT="${HOME?}/.grds/grds/client.crt"
export GRDS_CLIENT_CERT="${HOME?}/.grds/grds/client.crt"
export GRDS_CLIENT_KEY="${HOME?}/.grds/grds/client.key"
export GRDS_APISERVER_URL='https://127.0.0.1:8443'
export GRDS_NAMESPACE=grds
EOF

source ~/.bash_profile
```
