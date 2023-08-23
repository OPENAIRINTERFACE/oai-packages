# oai-gnb

KPT package for oai-gnb

## Usage

### Fetch the package

`kpt pkg get REPO_URI[.git]/PKG_PATH[@VERSION] oai-gnb`

Details: https://kpt.dev/reference/cli/pkg/get/

### View package content

`kpt pkg tree oai-gnb`

Details: https://kpt.dev/reference/cli/pkg/tree/

### Apply the package


```bash
kpt fn render oai-gnb
kpt live init oai-gnb 
kpt live apply oai-gnb --reconcile-timeout=2m --output=table
```

In case you want to install it on a particular cluster then use `--context` flag

Details: https://kpt.dev/reference/cli/live/
