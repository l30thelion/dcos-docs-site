---
layout: layout.pug
navigationTitle: konvoy up
title: konvoy up
menuWeight: 10
notes: Automatically generated, DO NOT EDIT
enterprise: false
excerpt: Run provision, and deploy (kubernetes, container-networking, and addons) to create or update a Kubernetes cluster reflecting the provided configuration and inventory files
---

## konvoy up

Run provision, and deploy (kubernetes, container-networking, and addons) to create or update a Kubernetes cluster reflecting the provided configuration and inventory files

### Synopsis

Run provision, and deploy (kubernetes, container-networking, and addons) to create or update a Kubernetes cluster reflecting the provided configuration and inventory files

```
konvoy up [flags]
```

### Options

```
      --addons-repositories strings   A comma separated list of addons repositories with uri@version (default [https://github.com/mesosphere/kubeaddons-kommander@testing-1.16-1.1.0-beta.2,https://github.com/mesosphere/kubeaddons-dispatch@stable-1.16-1.1.0,https://github.com/mesosphere/kubernetes-base-addons@stable-1.16-1.6.0])
      --cluster-name string           Name used to prefix the cluster and all the created resources (default "konvoy")
      --force-upgrade                 run an upgrade on all nodes requiring an upgrade ignoring upgrade safety checks
  -h, --help                          help for up
      --max-parallel-nodes string     set the number of nodes to upgrade in parallel. This can be an integer or a percentage of a nodePool. Set to 1 to run serially (requires --upgrade or --force-upgrade flag) (default "15%")
      --provisioner string            select a provisoner [aws|azure|gcp|docker|none] (default "aws")
      --skip-state-upload             skip the upload of the state to Kubernetes cluster
      --upgrade                       run an upgrade on all nodes requiring an upgrade
      --verbose                       enable debug level logging
      --without-draining              run an upgrade on all nodes requiring an upgrade, without draining the nodes first (requires --upgrade or --force-upgrade flag) (WARNING! usage can result in undefined behavior and service downtime)
  -y, --yes                           run command without prompting
```

### SEE ALSO

* [konvoy](../)	 - deploy and manage Kubernetes clusters
