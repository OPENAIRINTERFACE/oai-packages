# OpenAirInterface Radio Frequency Simulated gNB

## Description

Package represents OAI Radio Frequency Simulated gNB. You can check [here](https://gitlab.eurecom.fr/oai/openairinterface5g) to know more about OAI. 

Package definition is based on [OAI RFSIM GNB helm charts](https://gitlab.eurecom.fr/oai/cn5g/oai-cn5g-fed/-/tree/master/charts/oai-5g-ran/oai-gnb?ref_type=heads), 
and service level configuration is preserved as defined there. This package requires further specialization.

### Services

OAI RFSIM GNB project implements following services:

| Service | Description | Specialization |
| --- | --- | --- |
| rfsim-gNB | it represents 5G RAN - gNodeB | N2/N3 reference points - IPs and NADs |

### Dependencies

- It is possible to deploy `OAI-NR-UE` on another cluster than `oai-rfsim-gnb` but to reduce the networking complexity here it will be easy to allow `nr-ue` to communicate with `gNB` via K8s `ClusterIP` service. 
- `gNB` requires the ip-address of `AMF`. Here we are using `ipclaim.ipam.resource.nephio.org/v1alpha1` to get the ip-address of `AMF`. It is important to mention `nephio.org/action: get` in the `annotation`. 

### gNB Specialization

- `ngapIp` - it's N2 reference point, need to be aligned with `AMF` N2
- `gtpIp` - it's N3 reference point, need to be aligned with `UPF` N3
- `amfConfigs` - list of avaliable `AMF` NFs, be default it communicates with `AMF` via K8s `NodePort` service
- `NADs` need to be adjusted properly
- `k8s.v1.cni.cncf.io/networks` annotation need to be adjusted properly

## Usage

### Fetch the package

`kpt pkg get REPO_URI[.git]/PKG_PATH[@VERSION] oai-rfsim-gnb`

Details: https://kpt.dev/reference/cli/pkg/get/

### View package content

`kpt pkg tree oai-rfsim-gnb`

Details: https://kpt.dev/reference/cli/pkg/tree/

### Apply the package

```
kpt live init oai-rfsim-gnb
kpt live apply oai-rfsim-gnb --reconcile-timeout=2m --output=table
```

Details: https://kpt.dev/reference/cli/live/
