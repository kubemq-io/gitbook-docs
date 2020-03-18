# Ack

Ack all messages in a 'queues' channel

## Synopsis

Ack command allows to clear / remove / ack all messages in a 'queues' channel

```text
kubemqctl queues ack [flags]
```

## Examples

```text
    # Ack all messages in a 'queues' channel 'some-channel' with 2 seconds of wait to complete operation
    kubemqctl queue ack some-channel

    # Ack all messages in a 'queues' channel 'some-long-queue' with 30 seconds of wait to complete operation
    kubemqctl queue ack some-long-queue -w 30
```

## Options

```text
  -h, --help       help for ack
  -w, --wait int   set how many seconds to wait for ack all messages (default 2)
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

