# Quick Start

## **Welcome to KubeMQ!**

In this guide, we’ll walk you through how to install KubeMQ into your Kubernetes cluster.

Before we can do anything, we need to ensure you have access to a Kubernetes cluster running 1.12 or later, and a functioning kubectl command on your local machine. \(One easy option is to run Kubernetes on your local machine. We suggest [Docker Desktop](https://www.docker.com/products/docker-desktop) or [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/), but there are [many options](https://kubernetes.io/docs/setup/).\)

## Step 0:

### Obtain KubeMQ Registration Token

1. Please visit: [https://account.kubemq.io/login/register](https://account.kubemq.io/login/register) and register for a license token.
2. Wait for an email confirmation with your license token

## Step 1:

### Deploy KubeMQ package

```bash
kubectl apply -f https://get.kubemq.io/deploy?token=<kubemq-registration-token>
```

{% hint style="info" %}
If you get any errors such as "kind not found", run the command again
{% endhint %}

### Check Your KubeMQ Cluster Installation:

```bash
kubectl get kubemqclusters -n kubemq
```

## Step 2:

### Install kubemqctl CLI tool

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

## Step 3:

### Send 'Hello World'

```bash
kubemqctl queue send my-queue hello-world
```

### Get 'Hello World'

```bash
kubemqctl queue receive my-queue
```

## What's Next

### Learn KubeMQ Basics

{% page-ref page="../learn/the-basics/channels.md" %}

{% page-ref page="../learn/the-basics/smart-routing.md" %}

{% page-ref page="../learn/the-basics/grouping.md" %}

### Learn KubeMQ Message Patterns

{% page-ref page="../learn/message-patterns/queue.md" %}

{% page-ref page="../learn/message-patterns/pubsub.md" %}

{% page-ref page="../learn/message-patterns/rpc.md" %}

### Get started with KubeMQ message patterns

{% page-ref page="message-patterns/queues.md" %}

{% page-ref page="message-patterns/pubsub.md" %}

{% page-ref page="message-patterns/rpc.md" %}

