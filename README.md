# flavors-definition

This is a demo repo, lightweight copy of our internal-network project.
Refer to our [medium post explaining the original project](https://medium.com/@yoavshamia/managing-diverse-large-scale-k8s-clusters-with-a-flavor-based-approach-150934dfb1f3 )

this repo is the "what" and "where".
it says which apps belong to each flavor, and which clusters are in each env.

the structure is simple on purpose:

```text
<flavor>/
    hubApps.yaml
    edgeApps.yaml
    <env>/<clustername>.yaml
```

`hubApps.yaml` is the hub-side list. right now it has two entries only: `ca-bundle` and `hive`.

`edgeApps.yaml` is the edge workload list that `hive` consumes.

`<clustername>.yaml` is for per-cluster overrides, usually `clusterServer`.

## bootstrap reminder

bootstrap from the machine repo