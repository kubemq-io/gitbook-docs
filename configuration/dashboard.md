# Dashboard Configuration

## Basic

| Field | Type/Options | Description                               | Example |
|:------|:-------------|:------------------------------------------|:--------|
| port  | int          | Dashboard view port (expose via NodePort) | 32000   |

## Prometheus

| Field    | Type/Options | Description                  | Example |
|:---------|:-------------|:-----------------------------|:--------|
| nodePort | int          | Prometheus api port          | 31000   |
| image    | string       | Prometheus docker image name |         |


## Grafana

| Field        | Type/Options | Description                   | Example |
|:-------------|:-------------|:------------------------------|:--------|
| image        | string       | Grafana docker image name     |         |
| dashboardUrl | string       | Grafan dashboard download url |         |


