# Stream

Stream a message from a queue command

## Synopsis

Stream command allows to receive message from a queue in push mode response an appropriate action

```text
kubemqctl queues stream [flags]
```

## Examples

```text
    # Stream 'queues' message in transaction mode
    kubemqctl queue stream q1

    # Stream 'queues' message in transaction mode with visibility set to 120 seconds and wait time of 180 seconds
    kubemqctl queue stream q1 -v 120 -w 180
```

## Options

```text
  -h, --help             help for stream
  -v, --visibility int   set initial visibility seconds (default 30)
  -w, --wait int         set how many seconds to wait for 'queues' messages (default 60)
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

