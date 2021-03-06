# Receive

Receive a messages from a queue channel command

## Synopsis

Receive command allows to receive one or many messages from a queue channel

```text
kubemqctl queues receive [flags]
```

## Examples

```text
    # Receive 1 messages from a queue channel q1 and wait for 2 seconds (default)
    kubemqctl queue receive q1

    # Receive 3 messages from a queue channel and wait for 5 seconds
    kubemqctl queue receive q1 -m 3 -t 5

    # Watching 'queues' channel messages
    kubemqctl queue receive q1 -w
```

## Options

```text
  -h, --help               help for receive
  -m, --messages int       set how many messages we want to get from a queue (default 1)
  -t, --wait-timeout int   set how many seconds to wait for 'queues' messages (default 2)
  -w, --watch              set watch on 'queues' channel
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

