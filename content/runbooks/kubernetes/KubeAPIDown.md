# KubeAPIDown

## Meaning

The `KubeAPIDown` alert is triggered when all Kubernetes API servers have not
been reachable by the monitoring system for more than 15 minutes.

## Impact

This is a critical alert. The Kubernetes API is not responding. The
cluster may partially or fully non-functional.

## Diagnosis

Check the status of the API server targets in the Prometheus UI.

Then, confirm whether the API is also unresponsive for you:

```console
$ kubectl cluster-info
```

If you can still reach the API server, there may be a network issue between the
Prometheus instances and the API server pods. Check the status of the API server
pods.

```console
$ kubectl -n kube-system get pods
$ kubectl -n kube-system logs -l 'app=kube-apiserver'
```
## Mitigation

If you can still reach the API server intermittently, you may be able treat this
like any other failing deployment. If not, it's possible you may have to refer
to the disaster recovery documentation.
