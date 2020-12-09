# Kubemq azuresql Target Connector

Kubemq azuresql target connector allows services using kubemq server to access azuresql database services.

## Prerequisites
The following are required to run the azuresql target connector:
- access to db through azure firewall
- kubemq cluster
- azuresql server
- kubemq-targets deployment

## Configuration

azuresql target connector configuration properties:

| Properties Key                  | Required | Description                                 | Example                                                                |
|:--------------------------------|:---------|:--------------------------------------------|:-----------------------------------------------------------------------|
| connection                      | yes      | azuresql connection string address          | "server=server.net;user id=test;password=test;port=1433;database=initial_db;" |
| max_idle_connections            | no       | set max idle connections                    | "10"                                                                   |
| max_open_connections            | no       | set max open connections                    | "100"                                                                  |
| connection_max_lifetime_seconds | no       | set max lifetime for connections in seconds | "3600"                                                                 |


Example:

```yaml
bindings:
  - name: kubemq-query-azuresql
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-azuresql-connector"
        auth_token: ""
        channel: "query.azuresql"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: azure.stores.azuresql
      name: azure-stores-azuresql
      properties:
        connection: "server=server.net;user id=test;password=test;port=1433;database=initial_db;"
        max_idle_connections: "10"
        max_open_connections: "100"
        connection_max_lifetime_seconds: "3600"
```

## Usage

### Query Request

Query request metadata setting:

| Metadata Key | Required | Description      | Possible values |
|:-------------|:---------|:-----------------|:----------------|
| method          | yes      | set type of request | "query"      |

Query request data setting:

| Data Key | Required | Description  | Possible values    |
|:---------|:---------|:-------------|:-------------------|
| data     | yes      | query string | base64 bytes array |

Example:

Query string: `SELECT id,title,content,bignumber,boolvalue FROM post;`

```json
{
  "metadata": {
    "method": "query"
  },
  "data": "U0VMRUNUIGlkLHRpdGxlLGNvbnRlbnQsYmlnbnVtYmVyLGJvb2x2YWx1ZSBGUk9NIHBvc3Q7"
}
```

### Exec Request

Exec request metadata setting:

| Metadata Key    | Required | Description                            | Possible values    |
|:----------------|:---------|:---------------------------------------|:-------------------|
| method          | yes      | set type of request                    | "exec"             |
| isolation_level | no       | set isolation level for exec operation | ""                 |
|                 |          |                                        | "read_uncommitted" |
|                 |          |                                        | "read_committed"   |
|                 |          |                                        | "repeatable_read"  |
|                 |          |                                        | "serializable"     |
|                 |          |                                        |                    |


Exec request data setting:

| Data Key | Required | Description                   | Possible values     |
|:---------|:---------|:------------------------------|:--------------------|
| data     | yes      | exec string | base64 bytes array |

Example:

Exec string:

```sql
INSERT INTO post(ID,TITLE,CONTENT,BIGNUMBER,BOOLVALUE) VALUES
	                       (0,NULL,'Content One',1231241241231231123,true),
	                       (1,'Title Two','Content Two',123125241231231123,false);
```

```json
{
  "metadata": {
    "method": "exec",
    "isolation_level": "read_uncommitted"
  },
  "data": "SU5TRVJUIElOVE8gcG9zdChJRCxUSVRMRSxDT05URU5ULEJJR05VTUJFUixCT09MVkFMVUUpIFZBTFVFUwoJICAgICAgICAgICAgICAgICAgICAgICAoMCxOVUxMLCdDb250ZW50IE9uZScsMTIzMTI0MTI0MTIzMTIzMTEyMyx0cnVlKSwKCSAgICAgICAgICAgICAgICAgICAgICAgKDEsJ1RpdGxlIFR3bycsJ0NvbnRlbnQgVHdvJywxMjMxMjUyNDEyMzEyMzExMjMsZmFsc2UpOw==" 
}
```

### Transaction Request

Transaction request metadata setting:

| Metadata Key    | Required | Description                            | Possible values    |
|:----------------|:---------|:---------------------------------------|:-------------------|
| method          | yes      | set type of request                    | "transaction"             |
| isolation_level | no       | set isolation level for exec operation | ""                 |
|                 |          |                                        | "read_uncommitted" |
|                 |          |                                        | "read_committed"   |
|                 |          |                                        | "repeatable_read"  |
|                 |          |                                        | "serializable"     |


Transaction request data setting:

| Data Key | Required | Description                   | Possible values     |
|:---------|:---------|:------------------------------|:--------------------|
| data     | yes      | string string | base64 bytes array |

Example:

Transaction string:

```sql
DROP TABLE IF EXISTS post;
CREATE TABLE post (
         ID bigint,
         TITLE varchar(40),
         CONTENT varchar(255),
         BIGNUMBER bigint,
         BOOLVALUE boolean,
         CONSTRAINT pk_post PRIMARY KEY(ID)
       );
```

```json
{
  "metadata": {
    "key": "your-azuresql-key",
    "method": "delete"
  },
  "data": "RFJPUCBUQUJMRSBJRiBFWElTVFMgcG9zdDsKCSAgICAgICBDUkVBVEUgVEFCTEUgcG9zdCAoCgkgICAgICAgICBJRCBiaWdpbnQsCgkgICAgICAgICBUSVRMRSB2YXJjaGFyKDQwKSwKCSAgICAgICAgIENPTlRFTlQgdmFyY2hhcigyNTUpLAoJCQkgQklHTlVNQkVSIGJpZ2ludCwKCQkJIEJPT0xWQUxVRSBib29sZWFuLAoJICAgICAgICAgQ09OU1RSQUlOVCBwa19wb3N0IFBSSU1BUlkgS0VZKElEKQoJICAgICAgICk7"
}
```
