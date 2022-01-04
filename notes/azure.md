# Azure

## AKS

### CLI

```sh
# Add a cluster to kube config (C:\Users\<username>\.kube\config)
$ az aks get-credentials --name aks-aks-dev-01 -g rg-aks-dev-01 --admin
```

### Log Analytics queries

Query to get the **Events** for pods in a namespace.
Only events of type `Warning` and above are stored in Log Analytics

```kusto
// =~ is case insensitive string comparison
KubeEvents
| where ClusterName =~ '<cluster name>'
| where ObjectKind =~ 'Pod'
| where Namespace =~ '<namespace>'
| order by TimeGenerated desc 
| take 100
```
