# Set Cluster Security

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --tls-enabled | bool | false | Enable tls configuration |
| --tls-cert-data | string | "" | Set tls certification data |
| --tls-cert-file | string | "" | Set tls certification file name |
| --tls-key-data | string | "" | Set tls private key data |
| --tls-key-file | string | "" | Set tls private key file name |
| --tls-ca-data | string | "" | Set tls certification authority  data |
| --tls-ca-data | string | "" | Set tls certification authority  file name |

## Exmaple

Set TLS certificates to secure Kubemq cluster:

```bash
kubemqctl create cluster --tls-enabled --tls-cert-file ./cert.pem --tls-key-file ./key.pem --tls-ca-file ./ca.pem
```

Where cert.pem, key.pem and ca.pem are the required certificates/keys for TLS settings.
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| tls.cert | string | "" | Set tls certification data |
| tls.key | string | "" | Set tls private key data |
| tls.ca | string | "" | Set tls certification authority  data |

## Exmaple

Set TLS certificates to secure Kubemq cluster:

```bash
helm install kubemq-cluster --set-file tls.cert=./cert.pem,tls.key=./key.pem,tls.ca=./ca.pem kubemq-charts/kubemq
```

Where cert.pem, key.pem and ca.pem are the required certificates/keys for TLS settings.
{% endtab %}

{% tab title="yaml" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| cert | string | "" | Set tls certification data |
| key | string | "" | Set tls private key data |
| ca | string | "" | Set tls certification authority  data |

## Exmaple

Set TLS certificates to secure Kubemq cluster:

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
tls:
  # Server Certificate  
  cert: |-
    -----BEGIN CERTIFICATE-----
    MIIEbjCCAtagAwIBAgIQfYzCwf/wl8w4OtjN73CozzANBgkqhkiG9w0BAQsFADCB
    kTEeMBwGA1UEChMVbWtjZXJ0IGRldmVsb3BtZW50IENBMTMwMQYDVQQLDCpERVNL
    VE9QLUxOQjdQMjBcbGlvci5uYWJhdEBERVNLVE9QLUxOQjdQMjAxOjA4BgNVBAMM
    MW1rY2VydCBERVNLVE9QLUxOQjdQMjBcbGlvci5uYWJhdEBERVNLVE9QLUxOQjdQ
    MjAwHhcNMTkwNjAxMDAwMDAwWhcNMjkxMjI0MTUxNTEzWjBrMScwJQYDVQQKEx5t
    a2NlcnQgZGV2ZWxvcG1lbnQgY2VydGlmaWNhdGUxQDA+BgNVBAsMN0RFU0tUT1At
    TE5CN1AyMFxsaW9yLm5hYmF0QERFU0tUT1AtTE5CN1AyMCAoTGlvciBOYWJhdCkw
    ggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDyV2ZlFE0Tt8lG8tvabfk4
    W/Ch1EQm8jwGQnxENso5KqRgUvhGHfSpd7gXvdtTqMKJ1RT9PmgtM8fftrOgSRWR
    ZnJo5u8RbF3uLkwTvQGxNcmRmEPMXC+bST1oDbMBLtqlMsJDebSzY4zuv9etE1T2
    jA59yshOahL2KBck2ohg4SLhuBvTGGBANSGIulbmr9QtEGQ3qITGAIGZPFF8d/rP
    w5amtwSyaCKyNF2WemrxVzTo93f6igbpJLKI4CI2sZqFvyd5nJ3efgIoeo1pG8Yo
    2HtdM7VRFOLAnP/BhszXzvwBgDIKcJIAmtz+5sdYES7btNfTxaIlvKyMzy3xGNjT
    AgMBAAGjZzBlMA4GA1UdDwEB/wQEAwIFoDATBgNVHSUEDDAKBggrBgEFBQcDATAM
    BgNVHRMBAf8EAjAAMB8GA1UdIwQYMBaAFOYBUazACVSjah+t83pYZ/s0Hnv+MA8G
    A1UdEQQIMAaHBAAAAAAwDQYJKoZIhvcNAQELBQADggGBAERGliXrCZ8Xjupnzvpe
    oPJwM/cEFuoVt7ka3I9juh1/3pQjw1VhVDXiyKIX8LbdsalEdEQ3Nah1Y2CIOjUd
    RaSogP2ReTd5QPkQivssxlQTb+5cBHUM8V9/Fm596FZ29O612yrAeAM2N26r7Jkm
    CSsdvxl/ZZylsnknVGRIIHYpKJFOUI+nq4wFIVm7a/VZ8D/EOsJfraElO0x1+lDF
    txdoKAYGUymoqwX8v6+rv3jKyD6rON0jaYeUSLzKrdCNe1M5aQMxx2mql+rIHPOF
    ng5WLFLO0zyBjDFvAjeYN9ot4I7iMoexl7SNoVJgopGA/u7K/+f+LdB8xN/E4IX4
    DHczThCtLoTOkdlsAs2mESiitHSP/nXf5AJxpQTMG4chuxm7I14Y2KAdOHdtx5JN
    apnkNF8ieJUXlrrIqxLbd+ItBq3oP+z25P2p/lAr29Q8wydLFptXdnzmY/6PUbKP
    JgrLMeanOvBWBtKKHWN6tJEPTZt9GcFrtBnNJWhRxa8LHQ==
    -----END CERTIFICATE-----
  # Server Private Key
  key: |-
    -----BEGIN PRIVATE KEY-----
    MIIEvwIBADANBgkqhkiG9w0BAQEFAASCBKkwggSlAgEAAoIBAQDyV2ZlFE0Tt8lG
    8tvabfk4W/Ch1EQm8jwGQnxENso5KqRgUvhGHfSpd7gXvdtTqMKJ1RT9PmgtM8ff
    trOgSRWRZnJo5u8RbF3uLkwTvQGxNcmRmEPMXC+bST1oDbMBLtqlMsJDebSzY4zu
    v9etE1T2jA59yshOahL2KBck2ohg4SLhuBvTGGBANSGIulbmr9QtEGQ3qITGAIGZ
    PFF8d/rPw5amtwSyaCKyNF2WemrxVzTo93f6igbpJLKI4CI2sZqFvyd5nJ3efgIo
    eo1pG8Yo2HtdM7VRFOLAnP/BhszXzvwBgDIKcJIAmtz+5sdYES7btNfTxaIlvKyM
    zy3xGNjTAgMBAAECggEBAKHezS9Q+xbjmNcCGuXwtRn3F2kQvqEBBiTsPdLWggbj
    O753TQyQr76Oj/GTyC8+NwsXwBhTmgQvZR9CCwNSLczcECmPrzoFF0yjsf8xLTMw
    CT5t5UNYhBgGOLULCXkN0c+scuPdJFz6bsV+cNJTalnwPTG6xEbURWwUZTkhmxyR
    mAIt2isB1UvBvPUjNaNNf2VsfFSMT/RqW978xhNFu1RtSpTANdFqWs5pWRG0gwKC
    TgXOamazhvATvmJYcoJfQR9TDlMyAQ55sWPdWt9BdF3sXEqkyS2zatwvf0XKwBgN
    hvkwJyKm8vTKeVcc7KuOe7jrTKlruDvlelk4V2pJdFkCgYEA8xAxmngf1kfj04E2
    p6F6TS5YH5L3KKHI9fTAksIC1yLOS02oQr8cMi6vgVzmQoVd0uYnhHLk6xpe+lcj
    OGHvwB7knbhaKPJ/9DIsw37wE4mj8gwAyY9FDOHxPUSv00excoWTeMSX3PLzCXgO
    mqP8ovlW30yo1WNcxJlfmkZfoP8CgYEA/z1e7GTKL2utQAYfH0yVLi45eKrvT8Y8
    g8HcQvEOcwQD2CVrljn2wsV5Cdh0x1roWCIG3pTSNJCh5zNgW0j3SMH0QRLMK/5P
    YPpyH9rJzw8WKQFIyzcpdD6B3gBPebCZDejqLYuvEjcCvucnr70b2tq9tNl5h3Sy
    OOhigKyqdC0CgYEA53KDGUjLYBrCeVLv/T1JHRdFOIOUMC+mEXaGrPhrBfqRn6kJ
    0Mz0B2DnI/KXG76s8bbQ6FETZD+PMygoVHcFedaw8PJrf9QyPRBOCbXk22XUJBaD
    5Wo0YSkAssul9TSuZpOFMplY1j7NaDXXCi+e0H1G2IjBt7fOzTISk+/w/XcCgYAE
    X6XXwSZhx6ORXEl+PM61mt8rPSqaoFf7HgBLOVw5BlGWi5WbXmTnE4EudQITRHCE
    yhh6CezML8pGbu/wwIBUQ9aOoubSvinYDJKWDya0IJsNmtMHgGt6bXPGPRUfjbIh
    teMFYsZeNokaglWAwmnOxz7G8Y8OjiZbqUe+0radBQKBgQC+hmsXE/cpxhvGxsH2
    nw7LJq5nHecpltxIZfS5abf6GbXKILQnlm98QDva54jg9N4CtaavJMOw1AH6rlHS
    fzGT65B+/yDTvssTNxMSK7djPVQ4i+oeiMGhHJjihStDQhzEI+0lisk3z60oVq73
    CmRxliAhDXR5wgmEfBcPIRi+Mw==
    -----END PRIVATE KEY-----
  # CA Certificate for Mutual TLS  
  ca: |-
    -----BEGIN CERTIFICATE-----
    MIIE9DCCA1ygAwIBAgIRAMttD77JeToMiarbltEieXwwDQYJKoZIhvcNAQELBQAw
    gZExHjAcBgNVBAoTFW1rY2VydCBkZXZlbG9wbWVudCBDQTEzMDEGA1UECwwqREVT
    S1RPUC1MTkI3UDIwXGxpb3IubmFiYXRAREVTS1RPUC1MTkI3UDIwMTowOAYDVQQD
    DDFta2NlcnQgREVTS1RPUC1MTkI3UDIwXGxpb3IubmFiYXRAREVTS1RPUC1MTkI3
    UDIwMB4XDTE4MTEyNTE3Mjc0NloXDTI4MTEyNTE3Mjc0NlowgZExHjAcBgNVBAoT
    FW1rY2VydCBkZXZlbG9wbWVudCBDQTEzMDEGA1UECwwqREVTS1RPUC1MTkI3UDIw
    XGxpb3IubmFiYXRAREVTS1RPUC1MTkI3UDIwMTowOAYDVQQDDDFta2NlcnQgREVT
    S1RPUC1MTkI3UDIwXGxpb3IubmFiYXRAREVTS1RPUC1MTkI3UDIwMIIBojANBgkq
    hkiG9w0BAQEFAAOCAY8AMIIBigKCAYEAtmlegs3xrXi3Ccw4R281LP1C1Ra8IQBr
    4OcxeHV5jEOgjDAdX9GuU4m1Bb8zmYeR0/VOh4S7CX/10IMRnc18q9cLm5wTUfPl
    LG1Kr44jMdzjXq5lbJbqWD/AOfElBB2AMCALoQPUWYT523c0nxGJvjsVsL/+WHNQ
    kohToKhX3NppkaHv7u5GJXaGHGrf/p6H+TRL8gu8QPSDoX7aGPuad3j4FQq/3IyS
    vkZ1Or/ka8eTdPPGSjaWik7hOVBsKM4A/4nEGU7rIZDNGm9a88itsaWMh8O59oL9
    XJUK18Ff+Ja+JC6PaOQvKwKpA+U1oEz76MYQwVcYZignlIpEH8qAYT/QoNs+J/pZ
    8iL9wG6/LU5nQx88rbdoV72hQqphTyat0+hf6Uzgwy7RCRUkm0ElBrajom798mEV
    ptui95LKczr/2tMpdCpPRE096gh2Y6QfsNv4lJY3DiFY7BrJ+zKKeKc7+zEztd3B
    OsMhUaKbGNIO3JhG+RtnReQl5HLkPLjnAgMBAAGjRTBDMA4GA1UdDwEB/wQEAwIC
    BDASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQWBBTmAVGswAlUo2ofrfN6WGf7
    NB57/jANBgkqhkiG9w0BAQsFAAOCAYEAJhJ1dmazjkUXZ5CMFT0qF+NYmNHs2NRc
    WBDQa46VXuepu13IxAVdUSGLNUGK/H4WkKqS7bxiBUc/8lwrml6khI7j3c33EiDp
    tKIlaUugbczmIfsRAypbA45ZwluVX8fnQNBVKbz9Mf0gdsLzPLd5ReOo6g4AzNHS
    PsH2bb1o2hOG21d36stFtoUvcn4+Sa5/etFvZy++zu3ytsPdUjYBvpt9jRXa4+Tb
    DkuKBk3MW6dBYDsyx9CtThjuhQT4Q7i7Ds1hjntbGGYZgpL1ssbhMjpGaFTmwbS1
    RzisWhEtP8UJHv4SrrEDToWdd83aHpemp9j/NOr70r8H3BTW8tuaglqXStzvhX7x
    w+1Xp35MNUF+gJCnbZ8UjoBG+207Oc1DK7AIpgAF/ro0iVXMzSrgDCQOPmlK9tax
    obHstag0p3n8+TFVCUL5A1t6QBTsWiw/6PEwWnwT8+WrtBOl2J+I9wU3r6ZTct4H
    Qs2jN+XOsEMkxIj/qshAGNUCy8TjjSM6
    -----END CERTIFICATE-----
```
{% endtab %}
{% endtabs %}

