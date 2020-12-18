# Blob

Kubemq blob target connector allows services using kubemq server to access blob messaging services.

## Prerequisites

The following are required to run the blob target connector:

* kubemq cluster
* Azure active storage account
* Azure active with storage enable - with access account
* kubemq-targets deployment

## Configuration

blob target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| storage\_account | yes | azure storage account name | "my\_account" |
| storage\_access\_key | yes | azure storage access key | "abcd1234" |
| policy | no | azure blob retry policy | "retry\_policy\_exponential",retry\_policy\_fixed\(default retry\_policy\_fixed\) |
| max\_tries | no | try at most x times to perform the operation | "3" default \(1\) |
| try\_timeout | no | Maximum time allowed for any single try \(Millisecond\) | "600"default \(1000\) |
| retry\_delay | no | Backoff amount for each retry \(Millisecond\) | "60" default \(60\) |
| max\_retry\_delay | no | Max delay between retries \(Millisecond\) | "180"default \(180 |

Example:

```yaml
bindings:
  - name: kubemq-query-azure-blob
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-azure-blob-connector"
        auth_token: ""
        channel: "azure.storage.blob"
        group:   ""
        concurrency: "1"
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: azure.storage.blob
      name: azure-storage-blob
      properties:
        storage_account: "id"
        storage_access_key: "key"
```

## Usage

### Upload

Upload metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "upload" |
| file\_name | yes | the name to upload the file under | "myfile.txt" |
| service\_url | yes | service url path | "[https://test.blob.core.windows.net/test](https://test.blob.core.windows.net/test)" |
| data | yes | file data \(byte array\) | "bXktZmlsZS1kYXRh" |
| block\_size | no | specifies the block size to use | "0" ,default\(azblob.BlockBlobMaxStageBlockBytes\) |
| parallelism | no | maximum number of blocks to upload in parallel | "upload",default\(0\) |
| blob\_metadata | no | Key value string string of blob\_metadata | "{"tag":"test","name":"myname"}" |

Example:

```javascript
{
  "metadata": {
    "method": "upload",
    "file_name": "myfile.txt",
    "service_url": "https://test.end.point.test.net/test"
  },
  "data": "bXktZmlsZS1kYXRh"
}
```

### Delete

Delete metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "delete" |
| file\_name | yes | the name of the file to delete | "myfile.txt" |
| service\_url | yes | service url path | "[https://test.blob.core.windows.net/test](https://test.blob.core.windows.net/test)" |
| delete\_snapshots\_option\_type | no | type of method | "only","include","" \(default ""\) |

Example:

```javascript
{
  "metadata": {
    "method": "delete",
    "file_name": "myfile.txt",
    "service_url": "https://test.end.point.test.net/test"
  },
  "data": null
}
```

### get

For more information, see [https://docs.microsoft.com/rest/api/storageservices/get-blob](https://docs.microsoft.com/rest/api/storageservices/get-blob) get metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "get" |
| file\_name | yes | the name of the file to get | "myfile.txt" |
| service\_url | yes | service url path | "[https://test.blob.core.windows.net/test](https://test.blob.core.windows.net/test)" |
| max\_retry\_request | no | type of method | "20" \(default "1"\) |
| count | no | number of files to get | "20" \(will get all from offset\) |
| offset | no | start reading blob from offset | "20" \(will start from the first byte in blob\) |

Example:

```javascript
{
  "metadata": {
    "method": "get",
    "file_name": "myfile.txt",
    "service_url": "https://test.end.point.test.net/test"
  },
  "data": null
}
```

