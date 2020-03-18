---
title: Get Started
lang: en-US
description: Kubemq get started
tags:
  - pub/sub
  - message broker
  - KubeMQ
  - kubernetes
  - docker
  - cloud native
  - message queue
  - go
---

# Get Started

Kubemqctl is a command line interface \(CLI\) for [KubeMQ](https://kubemq.io) [Kubernetes](https://kubernetes.io/) Message Broker.

```bash
Usage:
  kubemqctl [command]

Available Commands:
  commands     Execute Kubemq 'commands' RPC commands
  config       Run Kubemqctl configuration wizard command
  create       Executes Kubemq create commands
  delete       Executes delete commands
  events       Execute Kubemq 'events' Pub/Sub commands
  events_store Execute Kubemq 'events_store' Pub/Sub commands
  get          Executes Kubemq get commands
  help         Help about any command
  queries      Execute Kubemq 'queries' RPC based commands
  queues       Execute Kubemq 'queues' commands
  scale        Executes Kubemq scale commands
  set          Executes set commands

Flags:
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
  -h, --help            help for kubemqctl

Use "kubemqctl [command] --help" for more information about a command.
```

## 

{% tabs %}
{% tab title="MacOS" %}
```bash
sudo curl -L https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl_darwin_amd64 -o /usr/local/bin/kubemqctl 
sudo chmod +x /usr/local/bin/kubemqctl
```
{% endtab %}

{% tab title="Linux  64 Bits" %}
```
sudo curl -L https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl_linux_amd64 -o /usr/local/bin/kubemqctl
sudo chmod +x /usr/local/bin/kubemqctl
```
{% endtab %}
{% endtabs %}

## Installation

 Copy and paste the following lines: \`\`\`bash sudo curl -L https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl\_darwin\_amd64 -o /usr/local/bin/kubemqctl sudo chmod +x /usr/local/bin/kubemqctl \`\`\` Copy and paste the following lines: \`\`\`bash sudo curl -L https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl\_linux\_amd64 -o /usr/local/bin/kubemqctl sudo chmod +x /usr/local/bin/kubemqctl \`\`\` Copy and paste the following lines: \`\`\`bash sudo curl -L https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl\_linux\_386 -o /usr/local/bin/kubemqctl sudo chmod +x /usr/local/bin/kubemqctl \`\`\` \#\#\#\#\# Option 1: - \[Download the latest kubemqctl.exe\]\(https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl.exe\). - Place the file under e.g. \`C:\Program Files\Kubemqctl\kubemqctl.exe\` - Add that directory to your system path to access it from any command prompt \#\#\#\#\# Option 2: Run in PowerShell as administrator: \`\`\`powershell New-Item -ItemType Directory 'C:\Program Files\Kubemqctl' Invoke-WebRequest https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl.exe -OutFile 'C:\Program Files\Kubemqctl\kubemqctl.exe' $env:Path += ';C:\Program Files\Kubemqctl' \`\`\`

