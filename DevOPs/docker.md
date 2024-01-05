---
---


[using extension fields to reuse variables](https://docs.docker.com/compose/compose-file/compose-file-v3/#extension-fields)

[dockerfile multi-stage build](https://docs.docker.com/build/building/multi-stage/)

### configuring a macvlan0
For the purposes of settig up a container that functionality acts the same as if a kvm virtual machine was configured to use a bridged networked interface. 

```bash

docker network create -d macvlan \
    --subnet=192.168.41.0./24 --gateway=192.168.41.1 \
    --ip-range 192.168.41.37/28 \
    -o parent=eth0 \
    --aux-address="myserver=" \
    macvlan0

```