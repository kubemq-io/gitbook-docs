# What's New

## What's new in KubeMQ Release v2

### KubeMQ Operator
KubeMQ Operator is a software extension to Kubernetes that make use of KubeMQ's custom resources to manage the lifecycle of KubeMQ applications and associated components.
KubeMQ release v2 introducing two core custom resources:
KubeMQCluster - manage KubeMQ server Statefulset deployment with associated config map, secrets, and services configuration.
KubeMQDashboard - manage Prometheus and Grafana based dashboard monitoring for KubeMQ clusters deployment.
KubeMQ Operator is deployed in a pre-defined namespace and manage the whole lifecycle of KubeMQ components within the namespace.
KubeMQ Operator is a certified Red Hat Openshift Operator.

### KubeMQ Server
Release v2 brings new features, enhancements to existing features together with performance improvements, mainly in messaging patterns that need storage such events store and queues. KubeMQ v2 is faster, stable, secured , and easy to manage than ever.

#### New Features
Authentication Access Control - allows controlling the access of clients to KubeMQ gRPC and Rest interfaces. Learn More.
Authorization Access Control - allows controlling the access of clients to KubeMQ server resources (Channels, Read, and Write). Learn More.
Notifications Access Control - allows getting an event for any access connection attempt. Learn More.
Smart Routing - In-flight and routing tables messaging allows to multicast messages to many destinations with a single message.

#### Enhancements to Existing Features
Inbound Traffic Control - allows controlling the messaging flow based on the state of cluster health (Circuit Breaker).
Cluster Security - simple TLS and mTLS configuration with the ability to control buffers and message size.
Persistent Store Configuration - In addition to simple PVC configuration, a Storage Class setting was added.
StatefulSet Deployment - Easy configurations to Health, Resources, and Node Selectors were added.

#### Performance Improvements
Write to Store Optimization - faster writing operation to the underlying file storage increased the sending rate of events store and queue messages dramatically.
Memory and CPU Optimization - reducing memory allocation and improvements to core algorithms increased the messaging processing throughput while reducing CPU and Memory consumptions
KubeMQ Dashboard
KubeMQ Dashboard is pre-configured Grafana/Prometheus deployment, which scrape KubeMQ Prometheus endpoints and present all KubeMQ's available metrics such messages counts and volumes, errors, clients information, channels data across al messaging patterns.
Learn More.

### Helm Charts
With the release of KubeMQ v2, helm charts repositories ware updated with the up-to-date KubeMQ's custom resources and configuration values.
Helm version 3 is required to install and manage KubeMQ charts.

### Kubemqctl
Kubemqctl is KubeMQ's CLI (Command Line Interface), which allows us to manage and control KubeMQ's applications and components with additional companion development tools that ease the development complexity of Kubernetes application based.

#### Key Features
Create, Update, and Delete KubeMQ applications and components such as KubeMQ Cluster and Dashboard.
Show Events Logs and configuration for KubeMQ Cluster
Set Port-Froward proxy to KubeMQ cluster to ease development cycle
Set and Manage Kubernetes contexts for quick context switching between Kubernetes environments
Attach command allows monitoring any channel in any message pattern messages content  in real-time
Full access to KubeMQ functions:
Queues - Send, Recieve, List, Attach, Stream, Peek and Ack-All
Events - Send, Receive, and Attach
Events Store - Send, Recieve, List and Attach
Commands - Send, Receive, and Attach
Queries - Send, Receive, and Attach

