---
description: >-
  Kubemq Dashboard is pre-configured Grafana/Prometheus deployment which scrape
  KubeMQ prometheus endpoints and present all Kubemq's available metrics.
---

# Dashboard

## Kubemq Dashboard Main View

![](../.gitbook/assets/dashboard-1.png)

  

![](../.gitbook/assets/dashboard-2.png)

## Exported Metrics

Kubemq exports the following metrics:

| Metric          | Tytp    | Labels                                         |
|:----------------|:--------|:-----------------------------------------------|
| Messages Count  | Counter | "node", "client_id", "type", "side", "channel" |
| Messages Volume | Counter | "node", "client_id", "type", "side", "channel" |
| Messages Errors | Counter | "node", "client_id", "type", "side", "channel" |
| Clients         | Gauge   | "node", "client_id", "type", "side", "channel" |

Labels Descriptions:


