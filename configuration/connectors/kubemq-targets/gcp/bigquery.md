# BigQuery

Kubemq gcp-bigquery target connector allows services using kubemq server to access google bigquery server.

## Prerequisites

The following are required to run the gcp-bigquery target connector:

* kubemq cluster
* gcp-bigquery set up
* kubemq-source deployment

## Configuration

bigquery target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| project\_id | yes | gcp bigquery project\_id | "/myproject" |
| credentials | yes | gcp credentials files | "&lt;google json credentials" |

Example:

```yaml
bindings:
  - name: kubemq-query-gcp-bigquery
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-gcp-bigquery-connector"
        auth_token: ""
        channel: "query.gcp.bigquery"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: gcp.bigquery
      name: gcp-bigquery
      properties:
        project_id: "id"
        credentials: 'json'
```

## Usage

### Query Request

query request.

Query metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "query" |
| query | yes | the query body | "select \* from table" |

Example:

```javascript
{
  "metadata": {
    "method": "query",
    "query": "select * from table"
  },
  "data": null
}
```

### Create Table Request

create a new table under data set

This method required a body of rows of string \[bigquery.TableMetadata\]

Example how to create the struct:

```go
    mySchema := bigquery.Schema{
            {Name: "name", Type: bigquery.StringFieldType},
            {Name: "age", Type: bigquery.IntegerFieldType},
        }

        metaData := &bigquery.TableMetadata{
            Schema:         mySchema,
            ExpirationTime: time.Now().AddDate(2, 1, 0), // Table will deleted in 2 years and 1 month.
        }
        bSchema, err := json.Marshal(metaData)
```

Create table metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "create\_table" |
| dataset\_id | yes | dataset to assign the table to | "your data set ID" |
| table\_name | yes | table name | "unique name" |

Example:

```javascript
{
  "metadata": {
    "method": "create_table",
    "dataset_id": "<mySet>",
    "table_name": "<myTable>"
  },
  "data": "eyJOYW1lIjoiIiwiTG9jYXRpb24iOiIiLCJEZXNjcmlwdGlvbiI6IiIsIlNjaGVtYSI6W3siTmFtZSI6Im5hbWUiLCJEZXNjcmlwdGlvbiI6IiIsIlJlcGVhdGVkIjpmYWxzZSwiUmVxdWlyZWQiOmZhbHNlLCJUeXBlIjoiU1RSSU5HIiwiUG9saWN5VGFncyI6bnVsbCwiU2NoZW1hIjpudWxsfSx7Ik5hbWUiOiJhZ2UiLCJEZXNjcmlwdGlvbiI6IiIsIlJlcGVhdGVkIjpmYWxzZSwiUmVxdWlyZWQiOmZhbHNlLCJUeXBlIjoiSU5URUdFUiIsIlBvbGljeVRhZ3MiOm51bGwsIlNjaGVtYSI6bnVsbH1dLCJNYXRlcmlhbGl6ZWRWaWV3IjpudWxsLCJWaWV3UXVlcnkiOiIiLCJVc2VMZWdhY3lTUUwiOmZhbHNlLCJVc2VTdGFuZGFyZFNRTCI6ZmFsc2UsIlRpbWVQYXJ0aXRpb25pbmciOm51bGwsIlJhbmdlUGFydGl0aW9uaW5nIjpudWxsLCJSZXF1aXJlUGFydGl0aW9uRmlsdGVyIjpmYWxzZSwiQ2x1c3RlcmluZyI6bnVsbCwiRXhwaXJhdGlvblRpbWUiOiIyMDIyLTExLTI1VDEwOjQxOjI1LjIyNjQ1NyswMjowMCIsIkxhYmVscyI6bnVsbCwiRXh0ZXJuYWxEYXRhQ29uZmlnIjpudWxsLCJFbmNyeXB0aW9uQ29uZmlnIjpudWxsLCJGdWxsSUQiOiIiLCJUeXBlIjoiIiwiQ3JlYXRpb25UaW1lIjoiMDAwMS0wMS0wMVQwMDowMDowMFoiLCJMYXN0TW9kaWZpZWRUaW1lIjoiMDAwMS0wMS0wMVQwMDowMDowMFoiLCJOdW1CeXRlcyI6MCwiTnVtTG9uZ1Rlcm1CeXRlcyI6MCwiTnVtUm93cyI6MCwiU3RyZWFtaW5nQnVmZmVyIjpudWxsLCJFVGFnIjoiIn0="
}
```

### Delete Table Request

delete a new table under data set

Delete table metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "create\_table" |
| dataset\_id | yes | dataset to assign the table to | "your data set ID" |
| table\_name | yes | table name | "unique name" |

Example:

```javascript
{
  "metadata": {
    "method": "delete_table",
    "dataset_id": "<mySet>",
    "table_name": "<myTable>"
  },
  "data":null
}
```

### Create Data Set Request

Create a Data Set

Create Data Set metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "create\_data\_set" |
| dataset\_id | yes | dataset to assign the table to | "your data set ID" |
| location | yes | dataset location to set | "US"  See [https://cloud.google.com/bigquery/docs/locations](https://cloud.google.com/bigquery/docs/locations) |

Example:

```javascript
{
  "metadata": {
    "method": "create_data_set",
    "dataset_id": "<mySet>",
    "location": "US"
  },
  "data":null
}
```

### Delete Data Set Request

delete a Data Set

Delete Data Set metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "delete\_data\_set" |
| dataset\_id | yes | dataset to assign the table to | "your data set ID" |

Example:

```javascript
{
  "metadata": {
    "method": "delete_data_set",
    "dataset_id": "<mySet>"
  },
  "data":null
}
```

### Get DataSets Request

get data sets.

Get DataSets setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "get\_data\_sets" |

Example:

```javascript
{
  "metadata": {
    "method": "get_data_sets"
  },
  "data": null
}
```

### Get Table Info

get basic information on a table by name

Get table Info

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "get\_table\_info" |
| dataset\_id | yes | dataset to assign the table to | "your data set ID" |
| table\_name | yes | table name | "unique table name" |

Example:

```javascript
{
  "metadata": {
    "method": "get_table_info",
    "dataset_id": "<mySet>",
    "table_name": "<myTable>"
  },
  "data": null
}
```

### Insert To Table

insert rows to table

Insert To Table this method required a body of rows as json array

```javascript
[
 {"id":"id-1","service":{"id":"service_id_1","value":0.1},"time":"1980-10-10T00:00:00Z"},
 {"id":"id-2","service":{"id":"service_id_2","value":0.1},"time":"1980-10-10T00:00:00Z"}
 ]
```

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "insert" |
| dataset\_id | yes | dataset to assign the table to | "your data set ID" |
| table\_name | yes | table name | "unique table name" |

Example:

```javascript
{
  "metadata": {
    "method": "insert",
    "dataset_id": "<mySet>",
    "table_name": "<myTable>"
  },
  "data": "W3sgIm5hbWUiOiJteU5hbWU0IiwgImFnZSI6MjV9XQ=="
}
```

