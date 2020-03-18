# Send

Send a message to a queue channel command

## Synopsis

Send command allows to send one or many message to a queue channel

```text
kubemqctl queues send [flags]
```

## Examples

```text
    # Send message to a queue channel channel
    kubemqctl queue send q1 some-message

    # Send message to a queue channel with metadata
    kubemqctl queue send q1 some-message --metadata some-metadata

    # Send 5 messages to a queues channel with metadata
    kubemqctl queue send q1 some-message --metadata some-metadata -m 5

    # Send message to a queue channel with a message expiration of 5 seconds
    kubemqctl queue send q1 some-message -e 5

    # Send message to a queue channel with a message delay of 5 seconds
    kubemqctl queue send q1 some-message -d 5

    # Send message to a queue channel with a message policy of max receive 5 times and dead-letter queue 'dead-letter'
    kubemqctl queue send q1 some-message -r 5 -q dead-letter
```

## Options

```text
  -q, --dead-letter-queue string   set dead-letter queue name
  -d, --delay int                  set queue message sending delay seconds
  -e, --expiration int             set queue message expiration seconds
  -h, --help                       help for send
  -r, --max-receive int            set dead-letter max receive count
  -m, --messages int               set dead-letter max receive count (default 1)
      --metadata string            set queue message metadata field
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

