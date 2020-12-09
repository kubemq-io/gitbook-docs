# KubeMQ Targets

KubeMQ Targets connects KubeMQ Message Broker with external systems and cloud services.

KubeMQ Targets allows us to build a message-based microservices architecture on Kubernetes with minimal efforts and without developing connectivity interfaces between KubeMQ Message Broker and external systems such as databases, cache, messaging, and REST-base APIs.

**Key Features**:

- **Runs anywhere**  - Kubernetes, Cloud, on-prem, anywhere
- **Stand-alone** - small docker container / binary
- **Single Interface** - One interface all the services
- **Any Service** - Support all major services types (databases, cache, messaging, serverless, HTTP, etc.)
- **Plug-in Architecture** Easy to extend, easy to connect
- **Middleware Supports** - Logs, Metrics, Retries, and Rate Limiters
- **Easy Configuration** - simple yaml file builds your topology

## Concepts

KubeMQ Targets building blocks are:
 - Binding
 - Source
 - Target
 - Request/Response

### Binding

Binding is a 1:1 connection between Source and Target. Every Binding runs independently.

![binding](.github/assets/learn-kubemq-targets-binding.jpeg)

### Target

Target is an external service that exposes an API allowing interacting and serve his functionalists with other services.

Targets can be Cache systems such as Redis and Memcached, SQL Databases such as Postgres and MySql, and even an HTTP generic Rest interface.

KubeMQ Targets integrate each one of the supported targets and service requests based on the request data.


### Source

The source is a KubeMQ connection (in subscription mode), which listens to requests from services and route them to the appropriate target for action, and return a response if needed.


### Request / Response

![concept](.github/assets/learn-kubemq-targets-concept.jpeg)

#### Request

A request is an object that sends to a designated target with metadata and data fields, which contains the needed information to perform the requested data.

##### Request Object Structure

| Field    | Type                  | Description                              |
|:---------|:----------------------|:-----------------------------------------|
| metadata | string, string object | contains metadata information for action |
| data     | bytes array           | contains raw data for action             |


##### Example

Request to get a data from Redis cache for the key "log"
```json
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


##### Response Object Structure

| Field    | Type                 | Description                                     |
|:---------|:---------------------|:------------------------------------------------|
| metadata | string, string object | contains metadata information result for action |
| data     | bytes array          | contains raw data result                        |
| is_error | bool                 | indicate if the action ended with an error      |
| error    | string               | contains error information if any               |


##### Example

Response received on request to get the data stored in Redis for key "log"
```json
{
  "metadata": {
    "result": "ok",
    "key": "log"
  },
  "data": "SU5TRVJUIElOVE8gcG9zdChJRCxUSVRMRSxDT05URU5UKSBWQUxVRVMKCSAgICAgICAgICAgICAgICAgICAgICA"
}
```
