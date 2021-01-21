---
title: "Install squids CLI"
linkTitle: "Squids CLI"
weight: 50
date: 2020-11-25
description: >
  Install squids CLI
---

`squidsctl` client is a command tool for k8s database operator management,we recommend using `squidsctl` to manage database operator in terminal console.
After database operator deployment,you can run following command to install `squidsctl`:

```shell
curl https://raw.githubusercontent.com/squids-io/grds/{{< param operatorVersion >}}/installers/kubectl/client-setup.sh > client-setup.sh
chmod +x client-setup.sh
./client-setup.sh
```
It will prompt for some environment variables,you should add these environment variables to bash profile:

```
cat <<EOF >> ~/.bash_profile
export SQUIDS_CA_CERT="${HOME?}/.squids/client.crt"
export SQUIDS_CLIENT_CERT="${HOME?}/.squids/client.crt"
export SQUIDS_CLIENT_KEY="${HOME?}/.squids/client.key"
export SQUIDS_APISERVER_URL='https://127.0.0.1:8443'
export SQUIDS_NAMESPACE=squids
EOF

source ~/.bash_profile
```
