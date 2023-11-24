# snapshot-test

Kotlin library to do simple snapshot testing.

This library is currently only distributed in Liflig
internal repositories.

## Regenrating failed snapshots
Use environment variables in order to regenerate snapshots. 
Set REGENERATE_SNAPSHOTS=true to regenerate all snapshots, and REGENERATE_FAILED_SNAPSHOTS=true in order to only regenerate failed snapshots.

## Contributing

This project follows
https://confluence.capraconsulting.no/x/fckBC

To check build before pushing:

```bash
mvn verify
```

The CI server will automatically release new version for builds on master.
