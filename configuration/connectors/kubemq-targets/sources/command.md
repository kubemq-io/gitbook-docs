# Command

Kubemq Command source provides rpc command subscriber for processing source commands.

## Prerequisites

The following are required to run command source connector:

* kubemq cluster
* kubemq-targets deployment

## Configuration

Command source connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| address | yes | kubemq server address \(gRPC interface\) | kubemq-cluster:50000 |
| client\_id | no | set client id | "client\_id" |
| auth\_token | no | set authentication token | jwt token |
| channel | yes | set channel to subscribe |  |
| group | no | set subscriber group |  |
| auto\_reconnect | no | set auto reconnect on lost connection | "false", "true" |
| reconnect\_interval\_seconds | no | set reconnection seconds | "5" |
| max\_reconnects | no | set how many time to reconnect | "0" |

Example:

```yaml
bindings:
  - name: kubemq-command-elastic-search
    source:
      kind: kubemq.command
      name: kubemq-command
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-command-elastic-search-connector"
        auth_token: ""
        channel: "command.elastic-search"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: stores.elastic-search
      name: target-elastic-search
      properties:
        urls: "http://localhost:9200"
        username: "admin"
        password: "password"
        sniff: "false"
```

