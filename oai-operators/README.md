# oai-operators

The package contains operator for OAI

- AMF
- SMF
- NRF
- UPF
- SMF
- UDR
- UDM
- AUSF

Nephio only proposed the CRD for AMF, SMF and UPF. We are using the same CRDs for network functions on service bus (UDR, UDM, AUSF and NRF). 

## Usage

### Fetch the package
`kpt pkg get https://gitlab.eurecom.fr/nephio/oai-packages/oai-operators@main`
Details: https://kpt.dev/reference/cli/pkg/get/

### View package content
`kpt pkg tree oai-operators`
Details: https://kpt.dev/reference/cli/pkg/tree/

### Apply the package

The default namespace is oai-operators

```
kpt live init oai-operators
kpt live apply oai-operators --reconcile-timeout=2m --output=table
```

Details: https://kpt.dev/reference/cli/live/
