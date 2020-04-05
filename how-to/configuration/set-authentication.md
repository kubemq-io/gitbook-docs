# Set Authentication

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --authentication-enabled --authentication-public-key-file ./key.pem --authentication-public-key-type "RS512"
```

Where key.pem is a public key file encoded with RSA 512.
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster --set-file authentication.key=./key.pem --set authentication.type=RS512 kubemq-charts/kubemq
```

Where key.pem is a public key file encoded with RSA 512.
{% endtab %}

{% tab title="yaml" %}

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

