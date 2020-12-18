# KubeMQ Targets

KubeMQ Targets connects KubeMQ Message Broker with external systems and cloud services.

KubeMQ Targets allows us to build a message-based microservices architecture on Kubernetes with minimal efforts and without developing connectivity interfaces between KubeMQ Message Broker and external systems such as databases, cache, messaging, and REST-base APIs.

**Key Features**:

* **Runs anywhere**  - Kubernetes, Cloud, on-prem, anywhere
* **Stand-alone** - small docker container / binary
* **Single Interface** - One interface all the services
* **Any Service** - Support all major services types \(databases, cache, messaging, serverless, HTTP, etc.\)
* **Plug-in Architecture** Easy to extend, easy to connect
* **Middleware Supports** - Logs, Metrics, Retries, and Rate Limiters
* **Easy Configuration** - simple yaml file builds your topology

## Concepts

KubeMQ Targets building blocks are:

* Binding
* Source
* Target
* Request/Response

### Binding

Binding is a 1:1 connection between Source and Target. Every Binding runs independently.

![binding](../../.gitbook/assets/learn-kubemq-targets-binding.jpeg)

### Target

Target is an external service that exposes an API allowing interacting and serve his functionalists with other services.

Targets can be Cache systems such as Redis and Memcached, SQL Databases such as Postgres and MySql, and even an HTTP generic Rest interface.

KubeMQ Targets integrate each one of the supported targets and service requests based on the request data.

### Source

The source is a KubeMQ connection \(in subscription mode\), which listens to requests from services and route them to the appropriate target for action, and return a response if needed.

### Request / Response

![concept](../../.gitbook/assets/learn-kubemq-targets-concept.jpeg)

#### Request

A request is an object that sends to a designated target with metadata and data fields, which contains the needed information to perform the requested data.

**Request Object Structure**

| Field | Type | Description |
| :--- | :--- | :--- |
| metadata | string, string object | contains metadata information for action |
| data | bytes array | contains raw data for action |

**Example**

Request to get a data from Redis cache for the key "log"

```javascript
{
  "metadata": {
    "method": "get",
    "key": "log"
  },
  "data": null
}
```

#### Response

The response is an object that sends back as a result of executing an action in the target

**Response Object Structure**

| Field | Type | Description |
| :--- | :--- | :--- |
| metadata | string, string object | contains metadata information result for action |
| data | bytes array | contains raw data result |
| is\_error | bool | indicate if the action ended with an error |
| error | string | contains error information if any |

**Example**

Response received on request to get the data stored in Redis for key "log"

```javascript
{
  "metadata": {
    "result": "ok",
    "key": "log"
  },
  "data": "SU5TRVJUIElOVE8gcG9zdChJRCxUSVRMRSxDT05URU5UKSBWQUxVRVMKCSAgICAgICAgICAgICAgICAgICAgICA"
}
```

## Middlewares

In bindings configuration, KubeMQ Bridges supports middleware setting for each pair of source and target bindings.

These properties contain middleware information settings as follows:

### Logs Middleware

KubeMQ Bridges supports level based logging to console according to as follows:

| Property | Description | Possible Values |
| :--- | :--- | :--- |
| log\_level | log level setting | "debug","info","error" |
|  |  | "" - indicate no logging on this bindings |

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

| Property | Description | Possible Values |
| :--- | :--- | :--- |
| retry\_attempts | how many retries before giving up on target execution | default - 1, or any int number |
| retry\_delay\_milliseconds | how long to wait between retries in milliseconds | default - 100ms or any int number |
| retry\_max\_jitter\_milliseconds | max delay jitter between retries | default - 100ms or any int number |
| retry\_delay\_type | type of retry delay | "back-off" - delay increase on each attempt |
|  |  | "fixed" - fixed time delay |
|  |  | "random" - random time delay |

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

### Rate Limiter Middleware

KubeMQ Sources support a Rate Limiting of target executions.

Rate Limiter middleware settings values:

| Property | Description | Possible Values |
| :--- | :--- | :--- |
| rate\_per\_second | how many executions per second will be allowed | 0 - no limitation |
|  |  | 1 - n integer times per second |

An example for 100 executions per second:

```yaml
bindings:
  - name: sample-binding 
    properties: 
      rate_per_second: 100
    source:
    ......
```

