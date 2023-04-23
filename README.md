# Consul & Monk

This repository contains Monk.io template to deploy Consul either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

## Prerequisites

- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

## Make sure monkd is running

```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository

```bash
git clone https://github.com/monk-io/consul
```

## Load Template

```bash
cd consul
monk load MANIFEST
```

```bash
foo@bar:~$ monk list consul
runnable  consul/consul-client  local       -        -
runnable  consul/consul-node1   local       -        -
runnable  consul/consul-node2   local       -        -
group     consul/stack          local       -        -
```

## Deploy Stack

```bash
foo@bar:~$ monk run consul/stack
? Select tag to run [local/consul/stack] on: mnk
✔ Starting the job: local/consul/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% consul:latest mnk
✔ Checking/pulling images DONE
✔ Starting containers DONE
✔ Starting containers DONE
✔ Started local/consul/stack

🔩 templates/local/consul/stack
 └─🧊 Peer mnk
    ├─🔩 templates/local/consul/consul-node2
    │  └─📦 30dd768af08189d0ebba4cbe75f83507-onk-consul-consul-node2-consul
    │     ├─🧩 consul:latest
    │     ├─💾 /var/lib/monkd/volumes/consul-node2 -> /consul/data
    │     └─🔌 open 13.50.100.228:8501 (0.0.0.0:8501) -> 8500
    ├─🔩 templates/local/consul/consul-node1
    │  └─📦 abf89dc330eb304d80ad8541f92f461d-onk-consul-consul-node1-consul
    │     ├─🧩 consul:latest
    │     ├─💾 /var/lib/monkd/volumes/consul-node1 -> /consul/data
    │     ├─🔌 open udp 13.50.100.228:8301 (0.0.0.0:8301) -> 8301
    │     ├─🔌 open tcp 13.50.100.228:8600 (0.0.0.0:8600) -> 8600
    │     ├─🔌 open udp 13.50.100.228:8600 (0.0.0.0:8600) -> 8600
    │     ├─🔌 open tcp 13.50.100.228:8302 (0.0.0.0:8302) -> 8302
    │     ├─🔌 open tcp 13.50.100.228:8300 (0.0.0.0:8300) -> 8300
    │     ├─🔌 open tcp 13.50.100.228:8301 (0.0.0.0:8301) -> 8301
    │     ├─🔌 open 13.50.100.228:8500 (0.0.0.0:8500) -> 8500
    │     └─🔌 open udp 13.50.100.228:8302 (0.0.0.0:8302) -> 8302
    └─🔩 templates/local/consul/consul-client
       └─📦 f9a031ec73bff4183653ce86615da7a4-nk-consul-consul-client-client
          ├─🧩 consul:latest
          └─💾 /var/lib/monkd/volumes/consul-client -> /consul/data

💡 You can inspect and manage your above stack with these commands:
    monk logs (-f) local/consul/stack - Inspect logs
    monk shell     local/consul/stack - Connect to the container's shell
    monk do        local/consul/stack/action_name - Run defined action (if exists)
💡 Check monk help for more!

```

## Test Web UI

`http://13.50.100.228:8500/`

## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```
