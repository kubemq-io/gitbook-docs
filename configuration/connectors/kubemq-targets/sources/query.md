# Query

Kubemq Query source provides rpc query subscriber for processing source queries.

## Prerequisites

The following are required to run query source connector:

* kubemq cluster
* kubemq-targets deployment

## Configuration

Query source connector configuration properties:

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
  - name: kubemq-query-elastic-search
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-elastic-search-connector"
        auth_token: ""
        channel: "query.elastic-search"
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

