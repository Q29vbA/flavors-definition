# flavors-definition

The "what and where" repository. Defines flavors, the clusters that belong to each flavor, and the applications deployed to each.

## Directory structure

```
flavors-definition/
├── <flavor>/
│   ├── hubApps.yaml        # Hub-side apps (ca-bundle + hive). Consumed by the hive Helm chart.
│   ├── edgeApps.yaml       # Edge-side apps. Consumed by the hive Helm chart.
│   ├── <env>/
│   │   └── <clustername>.yaml   # Registers a cluster; holds per-cluster value overrides.
```

### Example

```
gpu-enabled/
├── hubApps.yaml
├── edgeApps.yaml
├── prod/
│   ├── gpu-cluster-1.yaml
│   └── gpu-cluster-2.yaml
└── dev/
    └── gpu-cluster-dev.yaml
```

## Bootstrap

Apply the root flavorset Application from the machine repo once to seed ArgoCD. After that, all ApplicationSets self-manage:

```bash
# From the flavors-machine repo root:
helm template flavorset ./flavorset --values ./flavorset/values.yaml | kubectl apply -n argocd -f -
```
