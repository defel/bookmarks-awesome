<<<<<<< HEAD
![Docker](http://blog.trifork.com/wp-content/uploads/2013/08/Docker-logo.png)

# Docker

- [LXC - Linux Containers](https://linuxcontainers.org/)

## CoreOS

- [coreos/etcd](https://github.com/coreos/etcd) - A highly-available key value store for shared configuration and service discovery
- [coreos/fleet](https://github.com/coreos/fleet) - A Distributed init System
- [SkyDNS](https://github.com/skynetservices/skydns) - SkyDNS is a distributed service for announcement and discovery of services built on top of etcd

### Articles

- [Quick Start](https://coreos.com/docs/quickstart/)
- [Getting Started with docker](https://coreos.com/docs/launching-containers/building/getting-started-with-docker/)
- [Getting Started with systemd](https://coreos.com/docs/launching-containers/launching/getting-started-with-systemd/)
- [Getting Started with etcd](https://coreos.com/docs/distributed-configuration/getting-started-with-etcd/)
- [Using Cloud-Config](https://coreos.com/docs/cluster-management/setup/cloudinit-cloud-config/)
- [Launching Containers with fleet](https://coreos.com/docs/launching-containers/launching/launching-containers-fleet/)
- [Fleet - Using the Client](https://coreos.com/docs/launching-containers/launching/fleet-using-the-client/)
- [Experimenting with CoreOS, confd, etcd, fleet, and CloudFormation](http://marceldegraaf.net/2014/04/24/experimenting-with-coreos-confd-etcd-fleet-and-cloudformation.html)

## Service Orchestration
- [Fig](http://www.fig.sh/index.html) - Fast, isolated development environments using Docker.
- [progrium/ambassadord](https://github.com/progrium/ambassadord) - A Docker ambassador (containerized TCP reverse proxy / forwarder) that supports static forwards, DNS-based forwards (with SRV), Consul+Etcd based forwards, or forwards based on the connecting container's intended backend (read: magic).
- [consul](http://www.consul.io/) -  Service discovery and configuration made easy. Distributed, highly available, and datacenter-aware.
- [gmr/consulate](https://github.com/gmr/consulate) - Consulate is a Python client library and set of application for the Consul service discovery and configuration system.
- [serf](http://www.serfdom.io/) - Serf is a decentralized solution for cluster membership, failure detection, and orchestration. Lightweight and highly available.
- [progrium/registrator](https://github.com/progrium/registrator) - Service registry bridge for Docker

## Deployment

- [Flynn](https://flynn.io/) - Flynn is the single platform that ops can provide to developers to power production, testing, and development, freeing developers to focus.
- [Deis](http://deis.io/) - Deis (pronounced DAY-iss) is an open source PaaS that makes it easy to deploy and manage applications on your own servers. Deis builds upon Docker and CoreOS to provide a lightweight PaaS with a Heroku-inspired workflow.
- [Stampede](https://github.com/cattleio/stampede) - Stampede is a hybrid IaaS/Docker orcherstration platform running on CoreOS. 

## Management

- [Panamax](http://panamax.io/) - Docker Management for Humans

## Fleet

- [Configuration](https://github.com/coreos/fleet/blob/master/Documentation/configuration.md)

## Dockerfile

> Set debian package tools (dpkg, apt-*) to non interactive, so no user prompt is expected
```bash
ENV DEBIAN_FRONTEND noninteractive
```
=======
![Docker](http://blog.trifork.com/wp-content/uploads/2013/08/Docker-logo.png)

# Docker

- [LXC - Linux Containers](https://linuxcontainers.org/)

## CoreOS

- [coreos/etcd](https://github.com/coreos/etcd) - A highly-available key value store for shared configuration and service discovery
- [coreos/fleet](https://github.com/coreos/fleet) - A Distributed init System
- [SkyDNS](https://github.com/skynetservices/skydns) - SkyDNS is a distributed service for announcement and discovery of services built on top of etcd

### Articles

- [Quick Start](https://coreos.com/docs/quickstart/)
- [Getting Started with docker](https://coreos.com/docs/launching-containers/building/getting-started-with-docker/)
- [Getting Started with systemd](https://coreos.com/docs/launching-containers/launching/getting-started-with-systemd/)
- [Getting Started with etcd](https://coreos.com/docs/distributed-configuration/getting-started-with-etcd/)
- [Using Cloud-Config](https://coreos.com/docs/cluster-management/setup/cloudinit-cloud-config/)
- [Launching Containers with fleet](https://coreos.com/docs/launching-containers/launching/launching-containers-fleet/)
- [Fleet - Using the Client](https://coreos.com/docs/launching-containers/launching/fleet-using-the-client/)
- [Experimenting with CoreOS, confd, etcd, fleet, and CloudFormation](http://marceldegraaf.net/2014/04/24/experimenting-with-coreos-confd-etcd-fleet-and-cloudformation.html)

## Service Orchestration
- [Fig](http://www.fig.sh/index.html) - Fast, isolated development environments using Docker.
- [progrium/ambassadord](https://github.com/progrium/ambassadord) - A Docker ambassador (containerized TCP reverse proxy / forwarder) that supports static forwards, DNS-based forwards (with SRV), Consul+Etcd based forwards, or forwards based on the connecting container's intended backend (read: magic).
- [consul](http://www.consul.io/) -  Service discovery and configuration made easy. Distributed, highly available, and datacenter-aware.
- [gmr/consulate](https://github.com/gmr/consulate) - Consulate is a Python client library and set of application for the Consul service discovery and configuration system.
- [serf](http://www.serfdom.io/) - Serf is a decentralized solution for cluster membership, failure detection, and orchestration. Lightweight and highly available.
- [progrium/registrator](https://github.com/progrium/registrator) - Service registry bridge for Docker

## Deployment

- [Flynn](https://flynn.io/) - Flynn is the single platform that ops can provide to developers to power production, testing, and development, freeing developers to focus.
- [Deis](http://deis.io/) - Deis (pronounced DAY-iss) is an open source PaaS that makes it easy to deploy and manage applications on your own servers. Deis builds upon Docker and CoreOS to provide a lightweight PaaS with a Heroku-inspired workflow.

## Management

- [Panamax](http://panamax.io/) - Docker Management for Humans

## Fleet

- [Configuration](https://github.com/coreos/fleet/blob/master/Documentation/configuration.md)

## Dockerfile

> Set debian package tools (dpkg, apt-*) to non interactive, so no user prompt is expected
```bash
ENV DEBIAN_FRONTEND noninteractive
```

---

>>>>>>> moar links