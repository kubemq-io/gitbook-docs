# KubeMQ Bridges

## Configuration

KubeMQ Bridges loads configuration file on startup. The configuration file is a yaml file that contains definitions for bindings of Sources and Targets.

The default config file name is config.yaml, and KubeMQ bridges search for this file on loading.

### Structure

Config file structure:

```yaml

bindings:
  - name: clusters-sources # unique binding name
    properties: # Bindings properties such middleware configurations
      log_level: error
      retry_attempts: 3
      retry_delay_milliseconds: 1000
      retry_max_jitter_milliseconds: 100
      retry_delay_type: "back-off"
      rate_per_second: 100
    sources:
      kind: source.query # Sources kind
      name: name-of-sources # sources name 
      connections: # Array of connections settings per each source kind
        - .....
    targets:
      kind: target.query # Targets kind
      name: name-of-targets # targets name
      connections: # Array of connections settings per each target kind
        - .....
```

### Targets

| Type                                                                              | Kind                | Configuration                           |
|:----------------------------------------------------------------------------------|:--------------------|:----------------------------------------|
| [Queue](https://docs.kubemq.io/learn/message-patterns/queue)                      | kubemq.queue        | [Usage](./targets/queue.md)        |
| [Events](https://docs.kubemq.io/learn/message-patterns/pubsub#events)             | kubemq.events       | [Usage](./targets/events.md)       |
| [Events Store](https://docs.kubemq.io/learn/message-patterns/pubsub#events-store) | kubemq.events-store | [Usage](./targets/events-store.md) |
| [Command](https://docs.kubemq.io/learn/message-patterns/rpc#commands)             | kubemq.command      | [Usage](./targets/command.md)      |
| [Query](https://docs.kubemq.io/learn/message-patterns/rpc#queries)                | kubemq.query        | [Usage](./targets/query.md)        |


### Sources

| Type                                                                              | Kind                | Configuration                           |
|:----------------------------------------------------------------------------------|:--------------------|:----------------------------------------|
| [Queue](https://docs.kubemq.io/learn/message-patterns/queue)                      | kubemq.queue        | [Usage](./sources/queue.md)        |
| [Events](https://docs.kubemq.io/learn/message-patterns/pubsub#events)             | kubemq.events       | [Usage](./sources/events.md)       |
| [Events Store](https://docs.kubemq.io/learn/message-patterns/pubsub#events-store) | kubemq.events-store | [Usage](./sources/events-store.md) |
| [Command](https://docs.kubemq.io/learn/message-patterns/rpc#commands)             | kubemq.command      | [Usage](./sources/command.md)      |
| [Query](https://docs.kubemq.io/learn/message-patterns/rpc#queries)                | kubemq.query        | [Usage](./sources/query.md)        |


## Middlewares 

In bindings configuration, KubeMQ Bridges supports middleware setting for each pair of source and target bindings.

These properties contain middleware information settings as follows:

### Logs Middleware

KubeMQ Bridges supports level based logging to console according to as follows:

| Property  | Description       | Possible Values        |
|:----------|:------------------|:-----------------------|
| log_level | log level setting | "debug","info","error" |
|           |                   |  "" - indicate no logging on this bindings |

An example for only error level log to console:

```yaml
bindings:
  - name: sample-binding 
    properties: 
      log_level: error
    sources:
    ......  
```

### Retry Middleware

KubeMQ Bridges supports Retries' target execution before reporting of error back to the source on failed execution.

Retry middleware settings values:


| Property                      | Description                                           | Possible Values                             |
|:------------------------------|:------------------------------------------------------|:--------------------------------------------|
| retry_attempts                | how many retries before giving up on target execution | default - 1, or any int number              |
| retry_delay_milliseconds      | how long to wait between retries in milliseconds      | default - 100ms or any int number           |
| retry_max_jitter_milliseconds | max delay jitter between retries                      | default - 100ms or any int number           |
| retry_delay_type              | type of retry delay                                   | "back-off" - delay increase on each attempt |
|                               |                                                       | "fixed" - fixed time delay                  |
|                               |                                                       | "random" - random time delay                |

An example for 3 retries with back-off strategy:

```yaml
bindings:
  - name: sample-binding 
    properties: 
      retry_attempts: 3
      retry_delay_milliseconds: 1000
      retry_max_jitter_milliseconds: 100
      retry_delay_type: "back-off"
    sources:
    ......  
```
