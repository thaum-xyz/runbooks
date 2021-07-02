# KubePodNotReady

## Meaning

[This alert][KubePodNotReady] is fired when some pods have not been in the
`Ready` state for a certain period. This can have different reasons as described
[here][PodLifecycle]: When the pod is `Running` but not `Ready`, the `Readiness`
probe is failing. An application-specific error may prevent the pod from being
attached to a service. When the pod remains in `Pending` it can not be deployed
to particular namespaces and nodes.

## Impact

This pod is not functional and doesn't receive any traffic. Depending on how
many functional replicas are still available, the impact differs.

## Diagnosis

The notification details should list the pod that's not ready (and the pod's
namespace). E.g.:

```text
 - alertname = KubePodNotReady
...
 - namespace = openshift-logging
 - pod = elasticsearch-cdm-u1gqqbu6-2-868ddd4b45-w224d
...
```

Start by checking the status of the pod:

```console
$ kubectl get pod -n $NAMESPACE $POD
```

When the pod state is in `Running`, you can check its logs:

```console
$ kubectl logs -n $NAMESPACE $POD
```

Be aware there may be multiple containers in the pod. A check of all their logs
may be required. If the pod isn't running (for instance, if it's stuck in
`ContainerCreating`), then try to find out why.

## Mitigation

Try to find the issue in the logs before deleting it.

[PodLifecycle]: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/
