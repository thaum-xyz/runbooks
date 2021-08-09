# PlexExporterNoData

## Meaning

<!-- What this alert is about? -->

Plex exporter cannot retreive data from plex server.

## Impact

<!-- What this alert affects? -->

Lack of visibility into plex system.

## Diagnosis

<!-- How to check symptoms of the alert firing? -->

Query `{__name__=~"plex.*"}` in prometheus console. Check plex-exporter logs.

## Mitigation

<!-- How to solve the issue? -->

Rollover plex-exporter pod/container.
