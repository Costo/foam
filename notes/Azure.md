# Azure

## AKS

### Log Analytics queries

Query to get the **Events** for pods in a namespace.
Only events of type `Warning` and above are stored in Log Analytics

```
// =~ is case insensitive string comparison
KubeEvents
| where ClusterName =~ '<cluster name>'
| where ObjectKind =~ 'Pod'
| where Namespace =~ '<namespace>'
| order by TimeGenerated desc 
| take 100
```
