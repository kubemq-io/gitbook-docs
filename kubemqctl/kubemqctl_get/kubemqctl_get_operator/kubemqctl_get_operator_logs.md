# logs

Stream logs of Kubemq operator pods command

## Synopsis

Logs command allows to stream pods logs with powerful filtering capabilities

```text
kubemqctl get operator logs [flags]
```

## Examples

```text
    # Stream logs with selection of Kubemq operator
    kubemqctl get operator logs

    # Stream logs of all pods in default namespace
    kubemqctl get operator logs .* -n default

    # Stream logs of regex base pods with logs since 10m ago
    kubemqctl get operator logs kubemq-cluster.* -s 10m

    # Stream logs of regex base pods with logs since 10m ago include the string of 'connection'
    kubemqctl get operator logs kubemq-cluster.* -s 10m -i connection

    # Stream logs of regex base pods with logs exclude the string of 'error'
    kubemqctl get operator logs kubemq-operator.* -s 10m -e error

    # Stream logs of specific container
    kubemqctl get operator logs -c kubemq-cluster-0
```

## Options

```text
  -c, --container string      Set container regex
      --disable-color         Set to disable colorized output
  -e, --exclude stringArray   Set strings to exclude
  -h, --help                  help for logs
  -i, --include stringArray   Set strings to include
  -l, --label string          Set label selector
  -n, --namespace string      Set default namespace
  -s, --since duration        Set since duration time
  -t, --tail int              Set how many lines to tail for each pod
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

