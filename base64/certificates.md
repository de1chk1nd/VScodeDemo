https://kubernetes.io/docs/concepts/services-networking/ingress/

TLS
You can secure an Ingress by specifying a Secret that contains a TLS private key and certificate. The Ingress resource only supports a single TLS port, 443, and assumes TLS termination at the ingress point (traffic to the Service and its Pods is in plaintext). If the TLS configuration section in an Ingress specifies different hosts, they are multiplexed on the same port according to the hostname specified through the SNI TLS extension (provided the Ingress controller supports SNI). The TLS secret must contain keys named tls.crt and tls.key that contain the certificate and private key to use for TLS. For example:


apiVersion: v1
kind: Secret
metadata:
  name: testsecret-tls
  namespace: default
data:
  tls.crt: base64 encoded cert
  tls.key: base64 encoded key
type: kubernetes.io/tls

# # # # # # # # # # # # # # # # # # # # #
# # # # # # # # # # # # # # # # # # # # #

apiVersion: v1
kind: Secret
metadata:
  name: testsecret-tls
  namespace: default
data:
  tls.crt: base64 encoded cert
  tls.key: base64 encoded key
type: kubernetes.io/tls

-----------------------------------------

-----BEGIN CERTIFICATE-----
MIIDrjCCApagAwIBAgIEFFLXIzANBgkqhkiG9w0BAQsFADCBmDELMAkGA1UEBhMC
VVMxCzAJBgNVBAgTAldBMRAwDgYDVQQHEwdTZWF0dGxlMRIwEAYDVQQKEwlNeUNv
bXBhbnkxCzAJBgNVBAsTAklUMR4wHAYDVQQDExVsb2NhbGhvc3QubG9jYWxkb21h
aW4xKTAnBgkqhkiG9w0BCQEWGnJvb3RAbG9jYWxob3N0LmxvY2FsZG9tYWluMB4X
DTIwMTAyMTE4NDkwN1oXDTMwMTAxOTE4NDkwN1owgZgxCzAJBgNVBAYTAlVTMQsw
CQYDVQQIEwJXQTEQMA4GA1UEBxMHU2VhdHRsZTESMBAGA1UEChMJTXlDb21wYW55
MQswCQYDVQQLEwJJVDEeMBwGA1UEAxMVbG9jYWxob3N0LmxvY2FsZG9tYWluMSkw
JwYJKoZIhvcNAQkBFhpyb290QGxvY2FsaG9zdC5sb2NhbGRvbWFpbjCCASIwDQYJ
KoZIhvcNAQEBBQADggEPADCCAQoCggEBAKKya/Pb0BNdD9vv0KwE3OjM6krTshCN
jPqelzmVAFEcCbhbWNVp440yPMD3UD643zvSUDzKkonR/2U1FhHcNti2QNcXf9is
9zq6JVVKHASxsFbRJB6/3bxsJh8/+oy06lV8ktgBDMZ+JX8EcxjXQHCr+Qm71leE
kYYeqO3OPp7S8+DU840KVJpk71G/O0MUvKkiK8Uycxq0XxDx6P87mQJBSOVh+X2l
eNuXseBXZ/UoL+zmEWVJCqfjPnkVqL5XDxxQ6WnlxaqhcyFmk4ehdZzFpNZU5YKD
v2V/eniB+Qomu2YOtidGy3VU9xF7ZtP4Z+lt6+mJzQTLrGLivGUd47sCAwEAATAN
BgkqhkiG9w0BAQsFAAOCAQEAAxlhYaCflaShejudBq/2KXHNSeAtFtRMfiNjgqX9
Eo3oDu3K1R6M7Og+/lwv4ZVXpdWnjidJwG7vp5qJ8CjDUFfhLPqGNkvd7ybRpvAj
cieajnCCDmZ+vyagGHLnnLzSgDn5xfa5m0wZtLzRFMkHalKMFvXKttj93aT+wb6e
z3NDj+PSwbcGtiwgiJEs7VmSx21Btl1WOlSVfJ36oeBqTPar3Xx1z2nC3v86IpKs
RLw365t7OoiRgih8epHRsosit0iFfk7O1Hcc/c+nrZbRgHmbwFkENQlcRBqKG0y+
k+cq6n9c2FOy+PPc+d9v5ZsNlZixgm00nkM1KPm3CV18Gw==
-----END CERTIFICATE-----

-----BEGIN PRIVATE KEY-----
MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQCismvz29ATXQ/b
79CsBNzozOpK07IQjYz6npc5lQBRHAm4W1jVaeONMjzA91A+uN870lA8ypKJ0f9l
NRYR3DbYtkDXF3/YrPc6uiVVShwEsbBW0SQev928bCYfP/qMtOpVfJLYAQzGfiV/
BHMY10Bwq/kJu9ZXhJGGHqjtzj6e0vPg1PONClSaZO9RvztDFLypIivFMnMatF8Q
8ej/O5kCQUjlYfl9pXjbl7HgV2f1KC/s5hFlSQqn4z55Fai+Vw8cUOlp5cWqoXMh
ZpOHoXWcxaTWVOWCg79lf3p4gfkKJrtmDrYnRst1VPcRe2bT+Gfpbevpic0Ey6xi
4rxlHeO7AgMBAAECggEAPjtZJ5Hw6TczlcEJZIMHrNSU2cJX3hUG0+ZNmezwjhXX
cfke5aL3M08ABh+TRiqY2Nz9bANgQe9dbWz84CAHqqUr8BpBALRIbOI+3XzXcsQ0
20BsPIbPXf9QJavnPmMFL2XTFWRxaotd9FPTYrETKQXe4GZE+nzu3QplO3EkasNR
4AP7/GAgpKkYHVpvfMVX9Ai79vy8pBMbpOhGjXUT3nWwAspyEmpLnZnydnWuUEDS
tOfYhCTv12RUIx5bJabgxvmgv8FLHzM4TBsDUp+Lb2DWM+vBTxVeWzg6okip3oAa
mboyUOSx0GMWGlgmCTWQb1qmGqyNFE/7OG+9Npj8YQKBgQDUA15/hFnEPjpeXmEA
7B5j9oP9i3oKQDNoK3AM2udA9eMjo1yCHte3+Uxw8TXlqwpHwIip8TrGT1BUgrNk
uZ5YtU4gOVCDvvdDyVtTw7IX9MgV4DaExEcN7ZZSxRoowe0P/yP+R9BquHSgsqi5
uzf6k7cm7uF24UEDDo0+9kFxjQKBgQDEc7oO428x/bS1kS6hXmNn1q4xfwij/pNu
VqjV1V9RmVJGLV4ZfaQRHLuWYsXLl/FZ9e2WD+EhDJfch184QP5qsMJpLkZO3VgA
ibkmDgFw3b6tBLj6eCdlcU7EqE1CoHBQaa+7ZSvCmccmJ3MgcKmd2prQXMpTRUWh
r7k54s8EZwKBgQDA28+6b8q4mWK/NVtIW4HJrRWkLpx1drFMsTbcesSicwqMAK7G
LwhMcpr2onVE1rIjUyD+dlHg04VfWwWVOsSwLT1EUt7K+Yw0PZa2O+5lnGXmgG8X
lvSL1vRHlsSVDtN3GcDELs+IRQLSq7KQQZ5KctTItcSjP4TEIxiZjak6gQKBgFju
mrfKtbfHxlq7koRymkWTpd+6RksXH96/VEcZBMGHyvsB5qtbeT5V54W4yRnVeuji
r99S6PNxI/4tOinZIlNiGWBMFn/1K7Vyo2JazMQvXfYtQSAB7LO7i5DzL6aNwspk
Ta1jq1+5BbJ8AV4aIm7XW2Yf22e+4DrFtfBCgLzZAoGAF2MfGYnNtr0dSqmezMzu
ngfTM8zbCY8Ee4ggbGso0EbwMALK331d1cq2yM80r1xGkxQpPHKft4EEJwqHkUp7
vQoNv8U2V/zLd0xs5931NedYgOz1IH8A1u7JiH65DiPFduavexTeN3c+RzxCmpdE
Irurog+4c23pz+drph3iSeY=
-----END PRIVATE KEY-----