# NodeFilesystemAlmostOutOfFiles

## Meaning

This alert is similar to the [NodeFilesystemSpaceFillingUp][1] alert, but rather
than being based on a prediction that a filesystem will run out of inodes in a
certain amount of time, it uses simple static thresholds. The alert will fire as
at a `warning` level at 5% of available inodes left, and at a `critical` level
with 3% of available inodes left.

## Impact

A node's filesystem becoming full can have a far reaching impact, as it may
cause any or all of the applications scheduled to that node to experience
anything from performance degradation to full inoperability. Depending on the
node and filesystem involved, this could pose a critical threat to the stability
of the cluster.

## Diagnosis

Refer to the [NodeFilesystemFilesFillingUp][1] runbook.

## Mitigation

Refer to the [NodeFilesystemFilesFillingUp][1] runbook.

[1]: ./NodeFilesystemFilesFillingUp.md
