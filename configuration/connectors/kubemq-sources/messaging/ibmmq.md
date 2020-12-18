# IBM-MQ

Kubemq IBM-MQ Source connector allows services using kubemq server to access IBM-MQ messaging services.

## Prerequisites

The following are required to run the IBM-MQ Source connector:

* kubemq cluster
* IBM-MQ server
* kubemq-Sources deployment

## Configuration

IBM-MQ Source connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| queue\_manager\_name | yes | queue manager name \(QMName\) | "QM1" |
| host\_name | yes | set the host address or name | "localhost" |
| channel\_name | yes | ibm mq ChannelName to search the queue at | "DEV.APP.CHANNEL" |
| username | yes | Username to use to login to ibm-mq | "my\_user" |
| queue\_name | yes | the queue name to search under the channel | "my\_queue" |
| certificate\_label | no | unique identifier representing a digital certificate | "certificate label" |
| transport\_type | no | ibmmq transport\_type | "0"\(TransportType\_CLIENT\),"1"\(TransportType\_BINDINGS"\) |
| tls\_client\_auth | no | tls client auth type | "NONE","REQUIRED" |
| port\_number | no | ibmmq - server port number \(default 1414\) | "1414" |
| password | no | set ibmmq user password | "password" |
| key\_repository | no | the key\_repository a certificate store | "as123aq" |

Example:

```yaml
bindings:
  - name: kubemq-query-IBM-MQ
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-IBM-MQ-connector"
        auth_token: ""
        channel: "query.messaging.ibmmq"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    Source:
      kind: messaging.ibmmq
      name: messaging-ibmmq
      properties:
        queue_manager_name: "QM1"
        host_name: "localhost"
        channel_name: "DEV.APP.SVRCONN"
        username: "app"
        queue_name: "admin"
        password: "passw0rd"
        certificate_label: "NONE"
```

