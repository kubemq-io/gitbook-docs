# Cluster Proxy

Proxy Kubemq cluster connection to localhost command

## Synopsis

Proxy command allows to act as a full layer 4 proxy \(port-forwarding\) of a Kubemq cluster connection to localhost. Proxy a KubeMW cluster allows the developer to interact with remote Kubemq cluster ports as localhost

```text
kubemqctl set cluster proxy [flags]
```

## Examples

```text
    # Proxy a Kubemq cluster ports
    kubemqctl set cluster proxy
```

## Options

```text
  -h, --help   help for proxy
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

