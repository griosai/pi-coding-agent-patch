STATUS: LOCAL_CANDIDATE
SUMMARY: Pi 1.0.0-grios.2 retains the reviewed dependency correction and adds failure propagation before session teardown in both SDK and CLI dispatchers.

# Shutdown failure propagation

The archive identifies itself as `@griosai/pi-coding-agent@1.0.0-grios.2`.
It derives from the same official Pi 1.0.0 archive as grios.1, preserves the
brace-expansion 5.0.12 correction, and includes the original MIT license.

On `session_shutdown`, both dispatchers finish every handler, then rethrow the
first original failure. A diagnostic listener cannot replace that failure or
prevent remaining cleanup. The existing runtime therefore stops before
invalidation, disposal, or replacement. Other events retain their existing
error handling and cancellation behavior. This does not roll back cleanup
already completed by another handler.

Exactly four upstream members change: package identity, shrinkwrap metadata,
`dist/core/extensions/runner.js`, and
`dist/bundle/chunks/chunk-33XOIQ5N.js`. Modified runtime members omit stale
source-map references. All 1,239 other upstream members, including the original
source maps, remain byte-identical; the missing upstream license is added.
`build-provenance-grios.2.json` records source pins and each member's hashes.
No upstream lifecycle script ran during construction.

The reproducible builder and behavioral regression tests are maintained in the
consuming application's repository, which pins the builder and tests that match
this archive by commit. Both source archives and member bodies are
integrity-pinned; drift fails the build. The patch script's member sha256
values equal `shutdownPatch.members` in the provenance file.
The archive was not rebuilt during the 2026-10-04 salvage review; its hashes
were checked against the provenance file and the consumer lock only.

## Known issue: quit and signal shutdown

The rethrow also applies to `reason: "quit"`. Pi's interactive mode calls
`runtimeHost.dispose()` from `void this.shutdown(...)`, so a failing extension
shutdown handler becomes an uncaught exception, and `uncaughtCrash` exits with
code 1 at once because `isShuttingDown` is already set:

- SIGTERM/SIGHUP (`shutdown({ fromSignal: true })`): dispose runs before
  `ui.stop()`, so the process exits 1 with the terminal still in raw mode and
  `session.dispose()` skipped.
- Ctrl+D, double Ctrl+C, `/quit`: the TUI has already stopped, but the process
  exits 1 and `session.dispose()` is skipped.

grios.1 swallowed the failure and both paths exited 0 after full cleanup. The
consumer's shutdown lifecycle test expects `dispose()` to
reject, so the fix is a design choice: catch the rejection in the interactive
quit and signal callers (restore the terminal, then exit nonzero), or stop
rethrowing for `quit`. Either change needs a rebuilt archive with a new version
and a new consumer pin.

Use the raw GitHub URL at the full immutable commit containing the archive.

```text
SHA256: f5a43cd78991e3eab7e5e8e2d56fa435855b2a30991db295f3e7073bcd53866a
SRI: sha512-LDqye+u85xVLZscf6mGrRYZ1DHaA2M1d2EPlgdqfPR2JWzuc6w9kfeuKfk6njxMXuYCmbeaJlLHf1q7Ux3A6Kg==
```

The original grios.1 artifact and its provenance remain unchanged.
The derivative has not been published to the npm registry.
