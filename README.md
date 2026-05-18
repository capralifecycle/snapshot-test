# snapshot-test

Kotlin library to do simple snapshot testing.

This library is currently only distributed in Liflig
internal repositories.

## Regenerating snapshots

Regeneration is controlled by JVM system properties (e.g. `mvn test -D<prop>=true`):

- `REGENERATE_FAILED_SNAPSHOTS=true` — **preferred.** Runs the normal
  comparison and rewrites only snapshots whose assertion fails. Differences
  covered by JSON `ignoredPaths` do not trigger a rewrite, so non-deterministic
  values (timestamps, random UUIDs) cause no churn.
- `REGENERATE_SNAPSHOTS=true` — rewrites every snapshot the test run touches
  whose serialized value differs, **bypassing the comparison** (including
  `ignoredPaths`). Any snapshot holding a non-deterministic value is rewritten
  on every run, producing collateral diffs unrelated to your change. Use only
  for a deliberate mass refresh, and review the resulting diff.

Regeneration scope is whichever snapshot assertions the selected tests execute:
a full `mvn verify` touches every snapshot; narrowing the test selection
narrows which snapshots are (re)written.

## Contributing

This project follows
https://confluence.capraconsulting.no/x/fckBC

To check build before pushing:

```bash
mvn verify
```

The CI server will automatically release new version for builds on master.
