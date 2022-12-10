# Quick Start

## **Welcome to KubeMQ!**

In this guide, we’ll walk you through how to install KubeMQ into your Kubernetes cluster.

Before we can do anything, we need to ensure you have access to a Kubernetes cluster running 1.16 or later, and a functioning kubectl command on your local machine. (One easy option is to run Kubernetes on your local machine. We suggest [Docker Desktop](https://www.docker.com/products/docker-desktop) or [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/), but there are [many options](https://kubernetes.io/docs/setup/).)

## Step 0:

### Obtain KubeMQ License Key

1. Please visit: [https://account.kubemq.io/login/register](https://account.kubemq.io/login/register) and register for a license token.
2. Wait for an email confirmation with your license Key

## Step 1:

{% tabs %}
{% tab title="Kubernetes" %}
Run:

```bash
kubectl apply -f https://deploy.kubemq.io/init
```

```bash
kubectl apply -f https://deploy.kubemq.io/key/<license-key>
```
{% endtab %}

{% tab title="Docker" %}
Run:

```bash
docker run -it -p 8080:8080 -p 50000:50000 -p 9090:9090 -e KUBEMQ_TOKEN=<license-key> kubemq/kubemq
```
{% endtab %}
{% endtabs %}



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

## Step 4:

### Load KubeMQ Dashboard

```
kubemqctl get dashboard
```

<figure><img src="../.gitbook/assets/Snag_1237dbef.png" alt=""><figcaption><p>KubeMQ Dashboard</p></figcaption></figure>

## What's Next

### Build & Deploy KubeMQ Components

{% content-ref url="build-and-deploy.md" %}
[build-and-deploy.md](build-and-deploy.md)
{% endcontent-ref %}



### Learn KubeMQ Basics

{% content-ref url="../learn/the-basics/channels.md" %}
[channels.md](../learn/the-basics/channels.md)
{% endcontent-ref %}

{% content-ref url="../learn/the-basics/smart-routing.md" %}
[smart-routing.md](../learn/the-basics/smart-routing.md)
{% endcontent-ref %}

{% content-ref url="../learn/the-basics/grouping.md" %}
[grouping.md](../learn/the-basics/grouping.md)
{% endcontent-ref %}

### Learn KubeMQ Message Patterns

{% content-ref url="../learn/message-patterns/queue.md" %}
[queue.md](../learn/message-patterns/queue.md)
{% endcontent-ref %}

{% content-ref url="../learn/message-patterns/pubsub.md" %}
[pubsub.md](../learn/message-patterns/pubsub.md)
{% endcontent-ref %}

{% content-ref url="../learn/message-patterns/rpc.md" %}
[rpc.md](../learn/message-patterns/rpc.md)
{% endcontent-ref %}

### Get started with KubeMQ message patterns

{% content-ref url="message-patterns/queues.md" %}
[queues.md](message-patterns/queues.md)
{% endcontent-ref %}

{% content-ref url="message-patterns/pubsub.md" %}
[pubsub.md](message-patterns/pubsub.md)
{% endcontent-ref %}

{% content-ref url="message-patterns/rpc.md" %}
[rpc.md](message-patterns/rpc.md)
{% endcontent-ref %}

