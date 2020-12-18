# Queue

KubeMQ Bridges Queue target provides a queue sender for processing sources requests.

## Prerequisites

The following are required to run the queue target connector:

* kubemq cluster
* kubemq-bridges deployment

## Configuration

Queue target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| address | yes | kubemq server address \(gRPC interface\) | kubemq-cluster-a-grpc.kubemq.svc.cluster.local:50000 |
| client\_id | no | set client id | "client\_id" |
| auth\_token | no | set authentication token | JWT token |
| channels | no | set array of channels values to send the event | "queue.a,queue.b,queue.c" |
| expiration\_seconds | no | set default expiration seconds for each queue message | 0 - default, no expiration |
| delay\_seconds | no | set default delay seconds for each queue message | 0 - default, no delay |
| max\_receive\_count | no | set how many failed queue messages before routes to dead-letter queue | 0 - default, no routes to dead-letter queue |
| dead\_letter\_queue | no | set dead-letter queue | "dead-letter.queue.a" |

Example:

```yaml
bindings:
  - name:  queue-binding 
    properties: 
      log_level: error
      retry_attempts: 3
      retry_delay_milliseconds: 1000
      retry_max_jitter_milliseconds: 100
      retry_delay_type: "back-off"
      rate_per_second: 100
    sources:
    .....
    targets:
      kind: target.queue # Sources kind
      name: 3-clusters-targets # targets name 
      connections: # Array of connections settings per each target kind
        - address: "kubemq-cluster-a-grpc.kubemq.svc.cluster.local:50000"
          client_id: "cluster-a-queue-connection"
          auth_token: ""
          channels: "queue.a,queue.b,queue.c"
          expiration_seconds: 0
          delay_seconds: 0
          max_receive_count: 3
          dead_letter_queue: "dead-letter.queue.a"
        - address: "kubemq-cluster-b-grpc.kubemq.svc.cluster.local:50000"
          client_id: "cluster-b-queue-connection"
          auth_token: ""
          channels: "queue.a,queue.b,queue.c"
          expiration_seconds: 0
          delay_seconds: 0
          max_receive_count: 3
          dead_letter_queue: "dead-letter.queue.b"
        - address: "kubemq-cluster-c-grpc.kubemq.svc.cluster.local:50000"
          client_id: "cluster-c-queue-connection"
          auth_token: ""
          channels: "queue.a,queue.b,queue.c"
          expiration_seconds: 0
          delay_seconds: 0
          max_receive_count: 3
          dead_letter_queue: "dead-letter.queue.c"
```

