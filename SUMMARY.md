# Table of contents

* [Introduction](README.md)

## Getting Started

* [Create Cluster](getting-started/create-cluster/README.md)
  * [Kubemqctl](getting-started/create-cluster/kubemqctl.md)
  * [Helm](getting-started/create-cluster/helm.md)
  * [Openshift](getting-started/create-cluster/openshift.md)
* [Create Dashboard](getting-started/create-dashboard/README.md)
  * [Helm](getting-started/create-dashboard/helm.md)
  * [Openshift](getting-started/create-dashboard/openshift.md)
* [Queues](getting-started/queues.md)
* [Pub/Sub](getting-started/pubsub.md)
* [RPC](getting-started/rpc.md)

## Configuration

* [Cluster Configuration](configuration/cluster.md)
* [Dashboard Configuration](configuration/dashboard.md)

## Learn

* [The Basics](learn/the-basics.md)
* [Message Patterns](learn/message-patterns/README.md)
  * [Queues](learn/message-patterns/queue.md)
  * [Pub/Sub](learn/message-patterns/pubsub.md)
  * [RPC](learn/message-patterns/rpc.md)
* [Authentication](learn/authentication.md)
* [Authorization](learn/authorization.md)
* [Smart Routing](learn/smart-routing.md)

## Kubemqctl

* [Get Started](kubemqctl/get-started.md)
* [Create](kubemqctl/kubemqctl_create/README.md)
  * [Cluster](kubemqctl/kubemqctl_create/kubemqctl_create_cluster.md)
  * [Dashboard](kubemqctl/kubemqctl_create/kubemqctl_create_dashboard.md)
  * [Operator](kubemqctl/kubemqctl_create/kubemqctl_create_operator.md)
* [Get](kubemqctl/kubemqctl_get/README.md)
  * [Cluster](kubemqctl/kubemqctl_get/kubemqctl_get_cluster/README.md)
    * [Logs](kubemqctl/kubemqctl_get/kubemqctl_get_cluster/kubemqctl_get_cluster_logs.md)
    * [Events](kubemqctl/kubemqctl_get/kubemqctl_get_cluster/kubemqctl_get_cluster_events.md)
    * [Describe](kubemqctl/kubemqctl_get/kubemqctl_get_cluster/kubemqctl_get_cluster_describe.md)
  * [Dashboard](kubemqctl/kubemqctl_get/kubemqctl_get_dashboard/README.md)
    * [Describe](kubemqctl/kubemqctl_get/kubemqctl_get_dashboard/kubemqctl_get_cluster_describe.md)
  * [Operator](kubemqctl/kubemqctl_get/kubemqctl_get_operator/README.md)
    * [logs](kubemqctl/kubemqctl_get/kubemqctl_get_operator/kubemqctl_get_operator_logs.md)
* [Delete](kubemqctl/kubemqctl_delete/README.md)
  * [Cluster](kubemqctl/kubemqctl_delete/kubemqctl_delete_cluster.md)
  * [Dashboard](kubemqctl/kubemqctl_delete/kubemqctl_delete_dashboard.md)
  * [Operator](kubemqctl/kubemqctl_delete/kubemqctl_delete_operator.md)
* [Set](kubemqctl/kubemqctl_set/README.md)
  * [Cluster](kubemqctl/kubemqctl_set/kubemqctl_set_cluster.md)
  * [Cluster Proxy](kubemqctl/kubemqctl_set/kubemqctl_set_cluster_proxy.md)
  * [Context](kubemqctl/kubemqctl_set/kubemqctl_set_context.md)
* [Scale Cluster](kubemqctl/kubemqctl_scale_cluster.md)
* [Queues](kubemqctl/kubemqctl_queues/README.md)
  * [Send](kubemqctl/kubemqctl_queues/kubemqctl_queues_send.md)
  * [Receive](kubemqctl/kubemqctl_queues/kubemqctl_queues_receive.md)
  * [Attach](kubemqctl/kubemqctl_queues/kubemqctl_queues_attach.md)
  * [List](kubemqctl/kubemqctl_queues/kubemqctl_queues_list.md)
  * [Stream](kubemqctl/kubemqctl_queues/kubemqctl_queues_stream.md)
  * [Peek](kubemqctl/kubemqctl_queues/kubemqctl_queues_peek.md)
  * [Ack](kubemqctl/kubemqctl_queues/kubemqctl_queues_ack.md)
* [Events](kubemqctl/kubemqctl_events/README.md)
  * [Send](kubemqctl/kubemqctl_events/kubemqctl_events_send.md)
  * [Receive](kubemqctl/kubemqctl_events/kubemqctl_events_receive.md)
  * [Attach](kubemqctl/kubemqctl_events/kubemqctl_events_attach.md)
* [Events Store](kubemqctl/kubemqctl_events_store/README.md)
  * [Send](kubemqctl/kubemqctl_events_store/kubemqctl_events_store_send.md)
  * [Receive](kubemqctl/kubemqctl_events_store/kubemqctl_events_store_receive.md)
  * [Attach](kubemqctl/kubemqctl_events_store/kubemqctl_events_store_attach.md)
  * [List](kubemqctl/kubemqctl_events_store/kubemqctl_events_store_list.md)
* [Commands](kubemqctl/kubemqctl_commands/README.md)
  * [Send](kubemqctl/kubemqctl_commands/kubemqctl_commands_send.md)
  * [Receive](kubemqctl/kubemqctl_commands/kubemqctl_commands_receive.md)
  * [Attach](kubemqctl/kubemqctl_commands/kubemqctl_commands_attach.md)
* [Queries](kubemqctl/kubemqctl_queries/README.md)
  * [Send](kubemqctl/kubemqctl_queries/kubemqctl_queries_send.md)
  * [Receive](kubemqctl/kubemqctl_queries/kubemqctl_queries_receive.md)
  * [Attach](kubemqctl/kubemqctl_queries/kubemqctl_queries_attach.md)
* [Config](kubemqctl/kubemqctl_config.md)

## Development

* [SDK](development/sdk/README.md)
  * [.Net](https://github.com/kubemq-io/kubemq-CSharp)
  * [Java](https://github.com/kubemq-io/kubemq-Java)
  * [Go](https://github.com/kubemq-io/kubemq-go)
  * [Python](https://github.com/kubemq-io/kubemq-Python)
  * [Node](https://github.com/kubemq-io/kubemq-node)
  * [Rest](https://postman.kubemq.io/)
* [Examples](development/examples/README.md)
  * [.Net](https://github.com/kubemq-io/kubemq-CSharp/tree/master/Examples)
  * [Java](https://github.com/kubemq-io/kubemq-Java/tree/master/examples)
  * [Go](https://github.com/kubemq-io/kubemq-go/tree/master/examples)
  * [Python](https://github.com/kubemq-io/kubemq-Python/tree/master/examples)
  * [Node](https://github.com/kubemq-io/kubemq-node/tree/master/examples)

## Change Log

* [Kubemq Cluster](change-log/kubemq-cluster.md)
* [Kubemq Dashboard](change-log/kubemq-dashboard.md)
* [Kubemq Operator](change-log/kubemq-operator.md)

