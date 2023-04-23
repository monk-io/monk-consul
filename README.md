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
✔ Got the list
Type      Template     Repository  Version  Tags
runnable  consul/base  local       -        -
runnable  consul/node  local       -        -
```

## Deploy Stack

```bash
foo@bar:~$ monk run consul/node
? Template file /home/torin/monk-peer-review/monk-consul/consul.yml has been modified. Would you like to reload it? Yes
✔ Read file successfully
✔ Loaded /home/torin/monk-peer-review/monk-consul/consul.yml successfully

Please, update runnables using `monk update` command

Loaded 2 runnables, 0 process groups, 0 services, 0 entities and 0 entity instances
✨ Loaded:
 └─🔩 Runnables:
    ├─🧩 consul/base
    └─🧩 consul/node
✔ All templates loaded successfully
✔ Starting the run job: local/consul/node... DONE
✔ local/consul/node has been already running
💡 You can manage your stack with these commands:
        monk describe local/consul/node - Get detailed info about your runnable
        monk stop local/consul/node - Stop your runnable
        monk update local/consul/node - Update your runnable
        monk purge local/consul/node - Stop and clean your runnable
💡 Check monk help for more!

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/consul/node - Inspect logs
        monk shell     local/consul/node - Connect to the container's shell
        monk do        local/consul/node/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Test Web UI

`http://13.50.100.228:8500/`

## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```
