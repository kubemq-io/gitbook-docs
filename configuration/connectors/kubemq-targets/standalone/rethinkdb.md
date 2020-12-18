# ReThinkDB

Kubemq Rethinkdb target connector allows services using kubemq server to access Rethinkdb database services.

## Prerequisites

The following are required to run the Rethinkdb target connector:

* kubemq cluster
* Rethinkdb server
* kubemq-targets deployment

## Configuration

Rethinkdb target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| host | yes | Rethinkdb host address | "localhost:27017" |
| username | no | Rethinkdb username\(if user exists\) | "admin" |
| password | no | Rethinkdb password | "password" |
| timeout | no | timeout in seconds | "5" |
| keep\_alive\_period | no | keep alive period in seconds | "5" |
| auth\_key | no | auth key if needed for connection | "" |
| ssl | no | set if ssl is needed | "false","true" |
| cert\_file | no | ssl certificate file in string format | "my\_file" |
| cert\_key | no | ssl certificate key in string format | "my\_key" |
| handShakeVersion | no | server hand shake version | "1" |
| number\_of\_retries | no | number of retries for each request | "1" |
| initial\_cap | no | server initial cap | "0" |
| max\_open | no | max open for server | "0" |

Example:

```yaml
bindings:
  - name: kubemq-query-Rethinkdb
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-Rethinkdb-connector"
        auth_token: ""
        channel: "query.Rethinkdb"
        group:   ""
        concurrency: "1"
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: stores.Rethinkdb
      name: target-Rethinkdb
      properties:
        host: "localhost:27017"
        username: "admin"
        password: "password"
        database: "admin"
        collection: "test"
        write_concurrency: "majority"
        read_concurrency: ""
        params: ""
        operation_timeout_seconds: "2"
```

## Usage

### Get Request

Get request metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| key | no | key name | any string |
| method | yes | get | "get" |
| db\_name | yes | db name | "my\_db" |
| table | yes | table name | "my\_table" |

Example:

```javascript
{
  "metadata": {
    "key": "your-Rethinkdb-key",
    "db_name": "test",
    "table": "users",
    "method": "get"
  },
  "data": null
}
```

### Update Request

Update request metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| key | yes | key name | any string |
| method | yes | get | "update" |
| db\_name | yes | db name | "my\_db" |
| table | yes | table name | "my\_table" |

Update request data setting:

| Data Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| data | yes | map of string interface | base64 bytes array |

Example:

```javascript
{
  "metadata": {
    "key": "your-Rethinkdb-key",
    "db_name": "test",
    "table": "users",
    "method": "update"
  },
  "data": "ICAibWV0YWRhdGEiOiB7CiAgICAia2V5IjogInlvdXItUmV0aGlua2RiLWtleSIsCiAgICAiZGJfbmFtZSI6ICJ0ZXN0IiwKICAgICJ0YWJsZSI6ICJ1c2VycyIsCiAgICAibWV0aG9kIjogImdldCIKICB9LA==" 
}
```

### Delete Request

Delete request metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| key | yes | key name | any string |
| method | yes | get | "delete" |
| db\_name | yes | db name | "my\_db" |
| table | yes | table name | "my\_table" |

Example:

```javascript
{
  "metadata": {
    "key": "your-Rethinkdb-key",
        "db_name": "test",
        "table": "users",
        "method": "delete"
  },
  "data": null
}
```

### Insert Request

insert request metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| key | yes | key name | any string |
| method | yes | get | "insert" |
| db\_name | yes | db name | "my\_db" |
| table | yes | table name | "my\_table" |

Insert request data setting:

| Data Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| data | yes | map of string interface | base64 bytes array |

Example:

```javascript
{
  "metadata": {
    "key": "your-Rethinkdb-key",
    "db_name": "test",
    "table": "users",
    "method": "insert"
  },
  "data": "ICAibWV0YWRhdGEiOiB7CiAgICAia2V5IjogInlvdXItUmV0aGlua2RiLWtleSIsCiAgICAiZGJfbmFtZSI6ICJ0ZXN0IiwKICAgICJ0YWJsZSI6ICJ1c2VycyIsCiAgICAibWV0aG9kIjogImdldCIKICB9LA==" 
}
```

