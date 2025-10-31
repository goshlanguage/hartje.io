---
title: "Orchestrators"
date: 2022-04-27T22:32:07-05:00
draft: true
---

Relevant Technologies 
- Apache Mesos - Marathon (Container orchestration for Mesos) - Zookeeper
- DCOS - Operating System designed to run Mesos
- Kubernetes - etcd - can it use zookeeper to scale
- TalOS - Operating System designed to run kubernetes
- Slurm / Bright
- SUNK - Slurm on Kubernetes
- LFS

|References|Description|
|-|-|
|[Bright](https://slurm.schedmd.com/slurm_ug_2011/Bright_Computing_SLURM_integration.pdf)|Slurm cluster manager
|[Chubby](https://static.googleusercontent.com/media/research.google.com/en//archive/chubby-osdi06.pdf)|Lock service for distributed systems|
|[DCOS](https://dcos.io/)|Datacenter Operating System that provides Mesos|
|[DOCMA](https://www.diva-portal.org/smash/get/diva2:1435575/FULLTEXT01.pdf)|Decentralized Orchestration for Containerized Microservice Applications|
|[Marathon](https://mesosphere.github.io/marathon/)|A container orchestrator for Mesos|
|[Mesos Docs](https://mesos.apache.org/documentation/latest/)|Apache Mesos|
|[Kubernetes Limits](https://kubernetes.io/docs/setup/best-practices/cluster-large/)|And other considerations for large clusters|
|[Kubernetes big scale](https://openai.com/blog/scaling-kubernetes-to-7500-nodes/)|How to scale to 7500 nodes|
|[Rearchitecting kubernetes for the edge](https://dl.acm.org/doi/pdf/10.1145/3434770.3459730)|
|[SUNK](https://www.coreweave.com/blog/sunk-slurm-on-kubernetes-implementations)|Slurm on Kubernetes|
|[TalOS](https://www.talos.dev/)|Operating System for Kubernetes|
|[Tuning etcd](https://rancher.com/docs/rancher/v2.5/en/installation/resources/advanced/etcd/)|Maximize etcd performance|
|[Zookeeper](https://people.cs.umass.edu/~arun/590CC/papers/zookeeper.pdf)|Key Value store modeled after Chubby|
|[Zookeeper Atomic Broadcast](http://www.cs.cornell.edu/courses/cs6452/2012sp/papers/zab-ieee.pdf)|[Atomic broadcast](https://en.wikipedia.org/wiki/Atomic_broadcast) alternative to consensus|

- https://blog.pragmaticengineer.com/distributed-architecture-concepts-i-have-learned-while-building-payments-systems/
