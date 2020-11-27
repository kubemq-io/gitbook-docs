# Openshift

## Install KubeMQ operator

### Find KubeMQ Operator

1. Open Operators/OperatorHub
2. Goto Streaming & Messaging
3. Type KubeMQ in search box
4. Click on Kubemq Enterprise Operator

![](../../.gitbook/assets/openshift-1.png)

### Install KubeMQ Operator

1. Set Installation mode to A specific namespace on the cluster
2. Set the namespace
3. Click Subscribe

![](../../.gitbook/assets/openshift-2.png)

### Verify Operator Installation

![](../../.gitbook/assets/openshift-3.png)

![](../../.gitbook/assets/openshift-4.png)

## Install KubeMQ Dashboard

1. Click On Kubemq Dashboard 
2. Click on Create KubeMQDashboard
3. Click on Configure via YAML View
4. A yaml editor will open with default configuration will open
5. Click Create

Example:

```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqDashboard
metadata:
  name: kubemq-dashboard
  namespace: default
```

![](../../.gitbook/assets/openshift-dashboard-1.png)

### Verify KubeMQ Dashboard Installation

![](../../.gitbook/assets/openshift-dashboard-2.png)

## View Grafana Dashboard

### Add Route

1. Click on Networking and then on Routes
2. Click on Create Route

![](../../.gitbook/assets/openshift-dashboard-3.png)

3.  Set Route name

4. Select Kubemq-dashboard Service

![](../../.gitbook/assets/openshift-dashboard-4.png)

5. Set Target Port to 3000-&gt;3000\(TCP\)

![](../../.gitbook/assets/openshift-dashboard-5.png)

6. Click Create

### Configure Grafana Dashboard

1. Open the route link

![](../../.gitbook/assets/openshift-dashboard-6.png)

2. Click on the Home drop-down box

![](../../.gitbook/assets/openshift-dashboard-7.png)

3. Select Kubemq Dashboard

![](../../.gitbook/assets/openshift-dashboard-8.png)

4. Kubemq Dashboard will appear

![](../../.gitbook/assets/openshift-dashboard-9.png)

## Configuration

Check out dashboard configuration setting available:

{% page-ref page="../../configuration/dashboard/" %}

