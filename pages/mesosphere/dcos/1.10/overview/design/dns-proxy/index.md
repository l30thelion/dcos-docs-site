---
layout: layout.pug
excerpt:
title: >
    Design: Distributed DNS
navigationTitle: Distributed DNS
menuWeight: 3
---

## Background
Tasks move around frequently in DC/OS, resources must be dynamically resolved by an application protocol, and they are referred to by name. This means that DNS is an integral part of DC/OS. Rather than implementing a ZooKeeper or Mesos client in every project, we've chosen DNS as the lingua franca for discovery amongst all of our components in DC/OS.

This is implemented by using Mesos-DNS, which runs on each of the DC/OS masters. In the client systems, we put each of the masters into the `/etc/resolv.conf`. If a master goes down, DNS queries to that master will time out. DNS Forwarder (Spartan) solves this problem by dual-dispatching DNS queries to multiple masters and returning the first result.

To further alleviate risk, DNS Forwarder (Spartan) routes queries to nodes that it determines are most optimal to do a query. Specifically, if a domain ends in `mesos`, it will dispatch queries to the Mesos masters. If it doesn't end in `mesos`, it will send the query to 2 of the configured upstream nodes.

# Implementation
DNS Forwarder (Spartan) itself is very simple. It has dual-dispatch logic and hosts a domain `spartan` which has only one record -- `ready.spartan`. The purpose of this record is to investigate the availability of DNS Forwarder (Spartan). Many services, including ICMP, ping this address prior to starting.

DNS Forwarder (Spartan) learns its information from Exhibitor. For this reason, it is critical that Exhibitor is [configured correctly][1] on the masters. Alternatively, if the cluster is configured using static masters, it will load them from the static configuration file.

## ZooKeeper
DNS Forwarder (Spartan) also enables high availability of ZooKeepers. You can always use the addresses `zk-1.zk`, `zk-2.zk`, `zk-3.zk`, `zk-4.zk`, `zk-5.zk`. If there are fewer than 5 ZooKeepers, DNS Forwarder (Spartan) will point multiple records at a single ZooKeeper.

## Watchdog
Since DNS is such a specialized, sensitive subsystem we've chosen to protect it with a watchdog. There is a service installed on each node that runs every 5 minutes and checks whether or not it can query `ready.spartan`. To avoid harmonic effects, it sleeps for 1 minute past its initial start time to avoid racing spartan. You can monitor the system health of the watchdog as DNS Forwarder (Spartan) Watchdog in the system health [dashboard][2].

In addition to this watchdog, we also run genresolv, which checks whether or not DNS Forwarder (Spartan) is alive to generate the resolv.conf. If it believes DNS Forwarder (Spartan) not to be alive, it then rewrites the resolv.conf with the upstream resolvers that you've configured into your DC/OS cluster.

## DNS Forwarder Interface
DNS Forwarder (Spartan) creates its own network interface. This interface is actually a dummy device called `spartan`. This device hosts 3 IPs, `198.51.100.1/32`, `198.51.100.2/32`, `198.51.100.3/32`. You can monitor the health of the DNS Forwarder (Spartan) component in the system health [dashboard][2].

[1]: /mesosphere/dcos/1.10/installing/production/advanced-configuration/configuration-reference/
[2]: /mesosphere/dcos/1.10/monitoring/