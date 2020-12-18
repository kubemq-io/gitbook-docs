# MSSql

Kubemq mssql-aws target connector allows services using kubemq server to access mssql-aws database services.

## Prerequisites

The following are required to run the mssql target connector:

* kubemq cluster
* mssql server
* kubemq-targets deployment

## Configuration

Mssql target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| connection | yes | mssql connection string address | "sqlserver://sa:n8x2Nz!f@localhost:1433?database=master" |
| max\_idle\_connections | no | set max idle connections | "10" |
| max\_open\_connections | no | set max open connections | "100" |
| connection\_max\_lifetime\_seconds | no | set max lifetime for connections in seconds | "3600" |

Example:

```yaml
bindings:
  - name: kubemq-query-aws-mssql
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-mssql-connector"
        auth_token: ""
        channel: "query.aws.rds.mssql"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: aws.rds.mssql
      name: aws-rds-mssql
      properties:
        connection: "sqlserver://sa:n8x2Nz!f@localhost:1433?database=master"
        max_idle_connections: "10"
        max_open_connections: "100"
        connection_max_lifetime_seconds: "3600"
```

## Usage

### Query Request

Query request metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | set type of request | "query" |

Query request data setting:

| Data Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| data | yes | query string | base64 bytes array |

Example:

Query string: `SELECT id,title,content,bignumber,boolvalue FROM post;`

```javascript
{
  "metadata": {
    "method": "query"
  },
  "data": "U0VMRUNUIGlkLHRpdGxlLGNvbnRlbnQsYmlnbnVtYmVyLGJvb2x2YWx1ZSBGUk9NIHBvc3Q7"
}
```

### Exec Request

Exec request metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | set type of request | "exec" |
| isolation\_level | no | set isolation level for exec operation | "" |
|  |  |  | "read\_uncommitted" |
|  |  |  | "read\_committed" |
|  |  |  | "repeatable\_read" |
|  |  |  | "serializable" |
|  |  |  |  |

Exec request data setting:

| Data Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| data | yes | exec string | base64 bytes array |

Example:

Exec string:

```sql
INSERT INTO post(ID,TITLE,CONTENT,BIGNUMBER,BOOLVALUE) VALUES
                           (0,NULL,'Content One',1231241241231231123,true),
                           (1,'Title Two','Content Two',123125241231231123,false);
```

```javascript
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

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | set type of request | "transaction" |
| isolation\_level | no | set isolation level for exec operation | "" |
|  |  |  | "read\_uncommitted" |
|  |  |  | "read\_committed" |
|  |  |  | "repeatable\_read" |
|  |  |  | "serializable" |

Transaction request data setting:

| Data Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| data | yes | string string | base64 bytes array |

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

```javascript
{
  "metadata": {
    "key": "your-mssql-key",
    "method": "delete"
  },
  "data": "RFJPUCBUQUJMRSBJRiBFWElTVFMgcG9zdDsKCSAgICAgICBDUkVBVEUgVEFCTEUgcG9zdCAoCgkgICAgICAgICBJRCBiaWdpbnQsCgkgICAgICAgICBUSVRMRSB2YXJjaGFyKDQwKSwKCSAgICAgICAgIENPTlRFTlQgdmFyY2hhcigyNTUpLAoJCQkgQklHTlVNQkVSIGJpZ2ludCwKCQkJIEJPT0xWQUxVRSBib29sZWFuLAoJICAgICAgICAgQ09OU1RSQUlOVCBwa19wb3N0IFBSSU1BUlkgS0VZKElEKQoJICAgICAgICk7"
}
```

