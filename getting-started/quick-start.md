# Quick Start

**Welcome to KubeMQ!**

In this guide, we’ll walk you through how to install KubeMQ into your Kubernetes cluster.

Before we can do anything, we need to ensure you have access to a Kubernetes cluster running 1.12 or later, and a functioning kubectl command on your local machine. (One easy option is to run Kubernetes on your local machine. We suggest [Docker Desktop](https://www.docker.com/products/docker-desktop) or [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/), but there are [many options](https://kubernetes.io/docs/setup/).)

When ready, make sure you’re running a recent version of Kubernetes with:

```bash
kubectl version --short
```

## Install KubeMQ Cluster Community Edition

```bash
kubectl apply -f https://get.kubemq.io/deploy
```

## Install KubeMQ Cluster Enterprise Edition

```bash
kubectl apply -f https://get.kubemq.io/deploy?token=<your-license-token>
```

