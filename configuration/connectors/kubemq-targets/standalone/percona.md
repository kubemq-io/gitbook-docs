# Percona

Kubemq percona target connector allows services using kubemq server to access percona database services.

## Prerequisites

The following are required to run the percona target connector:

* kubemq cluster
* percona server
* kubemq-targets deployment

## Configuration

percona target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| connection | yes | percona connection string address | "root:percona@\(localhost:3306\)/store?charset=utf8&parseTime=True&loc=Local" |
| max\_idle\_connections | no | set max idle connections | "10" |
| max\_open\_connections | no | set max open connections | "100" |
| connection\_max\_lifetime\_seconds | no | set max lifetime for connections in seconds | "3600" |

Example:

```yaml
bindings:
- name: percona
  source:
    kind: kubemq.query
    properties:
      address: localhost:50000
      channel: query.percona
  target:
    kind: stores.percona
    properties:
      connection: root:root@(localhost:3306)/percona?charset=utf8&parseTime=True&loc=Local
  properties: {}
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
    "key": "your-percona-key",
    "method": "delete"
  },
  "data": "RFJPUCBUQUJMRSBJRiBFWElTVFMgcG9zdDsKCSAgICAgICBDUkVBVEUgVEFCTEUgcG9zdCAoCgkgICAgICAgICBJRCBiaWdpbnQsCgkgICAgICAgICBUSVRMRSB2YXJjaGFyKDQwKSwKCSAgICAgICAgIENPTlRFTlQgdmFyY2hhcigyNTUpLAoJCQkgQklHTlVNQkVSIGJpZ2ludCwKCQkJIEJPT0xWQUxVRSBib29sZWFuLAoJICAgICAgICAgQ09OU1RSQUlOVCBwa19wb3N0IFBSSU1BUlkgS0VZKElEKQoJICAgICAgICk7"
}
```

