# Set Authentication

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --authentication-enabled | bool | false | Enable authentication configuration |
| --authentication-public-key-data | string | "" | Set authentication public key data |
| --authentication-public-key-file | string | "" | Set authentication public key filename |
| --authentication-public-key-type | string | "" | Set authentication public key type |

authentication-public-key-type options: HS256/HS384/HS512/RS256/RS384/RS512/ES256/ES384/ES512

## Example

Load key.pem as a public key file encoded with RSA 512:

```bash
kubemqctl create cluster --authentication-enabled --authentication-public-key-file ./key.pem --authentication-public-key-type "RS512"
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| authentication.key | string | "" | Set authentication public key data |
| authentication.type | string | "" | Set authentication public key type |

authentication.type options:

HS256/HS384/HS512/RS256/RS384/RS512/ES256/ES384/ES512

## Example

Load key.pem as a public key file encoded with RSA 512:

```bash
helm install kubemq-cluster --set-file authentication.key=./key.pem --set authentication.type=RS512 kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| key | string | "" | Set JWT public key data |
| type | string | "" | Set JWT public key signing method |

type options:

HS256/HS384/HS512/RS256/RS384/RS512/ES256/ES384/ES512

## Example

Load key.pem as a public key file encoded with RSA 512:

Run:

```bash
kubectl apply -f {below-yaml-file}
```

```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqCluster
metadata:
  name: kubemq-cluster
  namesapce: kubemq
  labels:
    app: kubemq-cluster
spec:
  replicas: 3
  authentication:
    key: |-
      -----BEGIN PUBLIC KEY-----
      MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt2GVE6vIMKlUsJeIQrSX
      tPG7X+06/qfyfQUjYJYvn1Pff05B3LcazECYEMd/act5YlnzrMg6hlbcoa9szr3/
      mpwjJ+l4RKd6J1uZngPaGaRSAr4DvSYsMe9pRrrOnW9XyRBLiB+EOriq5qkcSTnR
      cwwoczPekJOK45rEUgdaL5JP/TRhYYwgayb+zQ5cu+1Hx94m5XldrAzkeQ8ldMeW
      BPzfasnX6zaBXtdWksJqmpMMWg1NunH3+NWFyLsPt4BNbtjpKOp7Wq3jDQpp803P
      sK3/XksM/87qPL4xNCJuV8MF4Pbx8JE3ZRusK6usmJrohv8+vgIIg4oKdpMjDlrz
      pQIDAQAB
      -----END PUBLIC KEY-----
    type: RS512
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
[Learn Access Control - Authentication Feature](../../learn/access-control/authentication.md)
{% endhint %}

