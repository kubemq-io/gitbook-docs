# List

Get a list of 'queues' channels / clients command

## Synopsis

List command allows to get a list of 'queues' channels / clients with details

```text
kubemqctl queues list [flags]
```

## Examples

```text
    # Get a list of queues / clients
    kubemqctl queue list

    # Get a list of queues / clients filtered by 'some-queue' channel only
    kubemqctl queue list -f some-queue
```

## Options

```text
  -f, --filter string   set filter for channel / client name
  -h, --help            help for list
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

