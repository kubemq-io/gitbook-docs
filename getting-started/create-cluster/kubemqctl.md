---
description: Kubemqctl is KubeMQ's CLI tool
---

# Kubemqctl



## Install Kubemqctl Tool

{% page-ref page="../../kubemqctl/get-started.md" %}

## Install KubeMQ Cluster Community Edition

```text
kubemqctl create cluster
```

## Install KubeMQ Cluster Enterprise Edition

### Install with license token

```text
kubemqctl create cluster -t {your-license-token}
```

### Install with license file

```text
kubemqctl create cluster --license-filename {your-license-filenam}
```

## Configuration

Check out cluster configuration setting available:

{% page-ref page="../../configuration/cluster/" %}



