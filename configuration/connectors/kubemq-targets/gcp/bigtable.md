# BigTable

Kubemq gcp-bigtable target connector allows services using kubemq server to access google bigtable server.

## Prerequisites

The following required to run the gcp-bigtable target connector:

* kubemq cluster
* gcp-bigtable set up
* kubemq-source deployment

## Configuration

bigtable target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| project\_id | yes | gcp bigtable project\_id | "/myproject" |
| credentials | yes | gcp credentials files | "&lt;google json credentials" |
| instance | yes | bigtable instance name | "&lt;bigtable instance name" |

Example:

```yaml
bindings:
  - name: kubemq-query-gcp-bigtable
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-gcp-bigtable-connector"
        auth_token: ""
        channel: "query.gcp.bigtable"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: gcp.bigtable
      name: gcp-bigtable
      properties:
        project_id: "id"
        credentials: 'json'
        instance:  "instance"
```

## Usage

### Create Column Family

Create Column Family:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "create\_column\_family" |
| column\_family | yes | the column\_family to create | "valid unique string" |
| table\_name | yes | the table name | "table name to assign the column family" |

Example:

```javascript
{
  "metadata": {
    "method": "create_column_family",
    "column_family": "valid_unique_string",
    "table_name": "valid_table_string"
  },
  "data": null
}
```

### Create Table

Create a table:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "create\_table" |
| table\_name | yes | the table name | "table name to delete or create" |

Example:

```javascript
{
  "metadata": {
    "method": "create_table",
    "table_name": "valid_table_string"
  },
  "data": null
}
```

### Delete Table

Delete the table:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "delete\_table" |
| table\_name | yes | the table name | "table name to delete or create" |

Example:

```javascript
{
  "metadata": {
    "method": "delete_table",
    "table_name": "valid_table_string"
  },
  "data": null
}
```

### Write Rows

Write new rows to table by column family

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "write" |
| table\_name | yes | the table name | "table name to delete or create" |
| column\_family | yes | the column\_family to create | "valid unique string" |

Example:

```javascript
{
  "metadata": {
    "method": "write",
    "column_family": "valid_unique_string",
    "table_name": "valid_table_string"
  },
  "data": "eyJpZCI6MSwibmFtZSI6InRlc3QxIiwic2V0X3Jvd19rZXkiOiIxIn0="
}
```

### Delete Rows

Delete rows from table by prefix

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "delete\_row" |
| table\_name | yes | the table name | "table name to delete or create" |
| row\_key\_prefix | yes | the row key | "valid unique string" |

Example:

```javascript
{
  "metadata": {
    "method": "delete_row",
    "row_key_prefix": "valid unique string",
    "table_name": "valid_table_string"
  },
  "data": null
}
```

### Get All Rows

Get all rows from the table:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "get\_all\_rows" |
| table\_name | yes | the table name | "table name to delete or create" |
| row\_key\_prefix | no | the row key | "valid unique string" |
| column\_name | no | the column to return | "column name" |

Example:

\`\`\`json { "metadata": { "method": "get\_all\_rows", "table\_name": "valid\_table\_string" }, "data": null }

