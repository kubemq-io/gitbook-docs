# Docker

## Configuration

By default, KubeMQ Docker container run with its default configurations. However, it is possible to mount a specific configuration file during the `docker run` command and mount it to the Docker container.

This feature allows users to customize the configuration according to their specific needs, ensuring that KubeMQ runs optimally in their environment. For example, a user may want to change the default port number or enable TLS encryption.

To take advantage of this feature, users need to create a configuration file in YAML format and mount it to the Docker container using the `--volume` flag. Once the container is running, KubeMQ will automatically detect the configuration file and use it instead of the default configuration.

This flexibility is particularly valuable for users with specific security or performance requirements, as it allows them to fine-tune KubeMQ to meet their needs. Additionally, it simplifies the deployment process by eliminating the need to manually configure KubeMQ after installation.

In order to run a docker container with specific configuration run the below command:

{% code overflow="wrap" %}
```docker
docker run -d -p 8080:8080 -p 50000:50000 -p 9090:9090 -v $(pwd)/config.yaml:/kubemq/config.yaml -e KUBEMQ_TOKEN=<license-key> kubemq/kubemq
```
{% endcode %}

## config.yaml

Configuration file example with the default values

```yaml
configdata: ""
api:
    enable: true
    port: 8080
authorization:
    enable: false
    policydata: ""
    filepath: ""
    url: ""
    autoreload: 0
authentication:
    enable: false
    jwtconfig:
        key: ""
        filepath: ""
        signaturetype: ""
    type: ""
    config: ""
security:
    cert:
        filename: ""
        data: ""
    key:
        filename: ""
        data: ""
    ca:
        filename: ""
        data: ""
routing:
    enable: false
    data: ""
    filepath: ""
    url: ""
    autoreload: 0
log:
    level: 2
    fileenable: false
    filepath: ""
store:
    cleanstore: false
    storepath: ./store
    maxqueues: 0
    maxsubscribers: 0
    maxmessages: 0
    maxqueuesize: 0
    maxretention: 1440
    maxpurgeinactive: 1440
queue:
    maxnumberofmessages: 1024
    maxwaittimeoutseconds: 3600
    maxexpirationseconds: 43200
    maxdelayseconds: 43200
    maxreceivecount: 1024
    maxvisibilityseconds: 43200
    defaultvisibilityseconds: 60
    defaultwaittimeoutseconds: 1
    maxinflight: 2048
    pubackwaitseconds: 60
connectors:
    grpc:
        enable: true
        port: "50000"
        subbuffsize: 100
        bodylimit: 104857600
    rest:
        enable: true
        port: "9090"
        readtimeout: 60
        writetimeout: 60
        subbuffsize: 100
        bodylimit: ""
        cors:
            alloworigins:
                - '*'
            allowmethods:
                - GET
                - POST
            allowheaders: []
            allowcredentials: false
            exposeheaders: []
            maxage: 0


```

