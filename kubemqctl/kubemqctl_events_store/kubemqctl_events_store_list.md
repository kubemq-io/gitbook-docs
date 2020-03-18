# List

Get a list of 'events store' channels / clients command

## Synopsis

List command allows to get a list of 'events store' channels / clients with details

```text
kubemqctl events_store list [flags]
```

## Examples

```text
    # Get a list of events store channels
    kubemqctl events_store list

    # Get a list of events stores channels/ clients filtered by 'some-events-store' channel only
    kubemqctl events_store list -f some-events-store
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

