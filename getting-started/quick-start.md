# Quick Start

## **Welcome to KubeMQ!**

In this guide, we’ll walk you through how to install KubeMQ into your Kubernetes cluster.

Before we can do anything, we need to ensure you have access to a Kubernetes cluster running 1.12 or later, and a functioning kubectl command on your local machine. \(One easy option is to run Kubernetes on your local machine. We suggest [Docker Desktop](https://www.docker.com/products/docker-desktop) or [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/), but there are [many options](https://kubernetes.io/docs/setup/).\)

When ready, make sure you’re running a recent version of Kubernetes with:

```bash
kubectl version --short
```

### Install KubeMQ Cluster Community Edition

Run:

```bash
kubectl apply -f https://get.kubemq.io/deploy
```

### Install KubeMQ Cluster Enterprise Edition

Run:

```bash
kubectl apply -f https://get.kubemq.io/deploy?token=<your-license-token>
```

{% hint style="info" %}
For free 30 days Enterprise licence Please [Register](https://account.kubemq.io/login/register)
{% endhint %}

### Check Your KubeMQ Cluster Installation

Run:

```bash
kubectl get kubemqclusters -n kubemq
```

### Check you KubeMQ Dashboard Installation

Run:

```bash
kubectl get kubemqdashboard -n kubemq
```

You can view Kubemq Dashboard at [http://localhost:32000 ](%20http://localhost:32000)

{% hint style="info" %}
If for some reason you get an error saying "... no matches for kind "KubemqCluster" .... ", please re-run the command again
{% endhint %}

## What next ?

### Install Kubemqctl tool

{% tabs %}
{% tab title="MacOS/Linux" %}
```bash
sudo curl -sL https://get.kubemq.io/install | sudo sh
```
{% endtab %}

{% tab title="Windows" %}
### Option 1:

* [Download the latest kubemqctl.exe](https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl.exe).
* Place the file under e.g. `C:\Program Files\kubemqctl\kubemqctl.exe`
* Add that directory to your system path to access it from any command prompt

### Option 2:

Run in PowerShell as administrator:

```bash
New-Item -ItemType Directory 'C:\Program Files\kubemqctl'
Invoke-WebRequest https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl.exe -OutFile 'C:\Program Files\kubemqctl\kubemqctl.exe'
$env:Path += ';C:\Program Files\kubemqctl'
```
{% endtab %}
{% endtabs %}

### Get started with:

{% page-ref page="message-patterns/queues.md" %}

{% page-ref page="message-patterns/pubsub.md" %}

{% page-ref page="message-patterns/rpc.md" %}

## Demo

{% embed url="https://player.vimeo.com/video/373966650" %}



