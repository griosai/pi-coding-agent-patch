STATUS: LOCAL_CANDIDATE
SUMMARY: Pi 1.0.0-grios.3 keeps grios.2's session_shutdown failure propagation and fixes its quit/signal issue: when cleanup fails, interactive shutdown now runs the session teardown steps the runtime never started for the current session (each at most once), restores the terminal, reports the failure and exits 1.

# Shutdown failure propagation

## grios.3 (current)

The archive identifies itself as `@griosai/pi-coding-agent@1.0.0-grios.3`.
It derives from the same official Pi 1.0.0 archive as grios.1 and grios.2,
preserves the brace-expansion 5.0.12 correction, and includes the original MIT
license.

### Dispatch (unchanged from grios.2)

On `session_shutdown`, both dispatchers finish every handler, then rethrow the
first original failure. A diagnostic listener cannot replace that failure or
prevent remaining cleanup. `AgentSessionRuntime.dispose()` therefore rejects
before invalidation, disposal or replacement, so SDK callers still see the
failure. Other events keep their existing error handling and cancellation
behavior. Cleanup already completed by another handler is not rolled back.

### Interactive quit and signal shutdown (new)

The orderly interactive exits reach `InteractiveMode.shutdown()`: Ctrl+C twice,
Ctrl+D, `/quit`, extension shutdown requests, the session selector's exit,
SIGTERM and SIGHUP. The fatal runtime error exit does not: it stops the TUI and
exits 1 directly, unchanged from upstream. In grios.2, `shutdown()` did not
handle the rejection. A failing handler made the process exit 1 without
disposing the session, and on SIGTERM/SIGHUP the terminal was left in raw mode.
grios.3 catches the rejection in that method and then:

1. Runs the teardown steps the runtime never started, each at most once.
   `AgentSessionRuntime.dispose()` emits the shutdown event, then calls its
   pre-invalidation hook (the interactive extension-UI reset), then
   `session.dispose()`. Before calling it, `shutdown()` installs its own hook,
   which records which session it ran for and how far the runtime got. If the
   event failed, both steps run. If the UI reset threw, only `session.dispose()`
   runs. If the runtime had started `session.dispose()`, nothing runs again.
   Progress recorded for another session does not count. A `/new`, `/resume`
   or `/fork` already running can tear down the outgoing session through the
   same hook and install a replacement while the failing handler runs. That
   replacement never reached teardown, so both steps run for it. Each step is
   guarded so one failure cannot skip the next. Neither step is safe to repeat: the UI reset
   calls extension widget disposers, and `session.dispose()` ends by running
   every registered session-resource cleanup.
2. Continues the unchanged path. Signal shutdown restores the terminal after
   cleanup; quit had already stopped the TUI.
3. Prints `pi session shutdown cleanup failed:` to stderr after the terminal
   is restored. The first failure follows unchanged, then any teardown errors.
4. Prints the resume hint (quit only, unchanged), then exits with status 1.

A successful shutdown is unchanged and exits 0.

### Members

Exactly five upstream members change:

- package identity;
- shrinkwrap metadata;
- `dist/core/extensions/runner.js`: byte-identical to grios.2;
- `dist/bundle/chunks/chunk-33XOIQ5N.js`: the grios.2 dispatcher plus the
  interactive shutdown change; this chunk is the packaged `pi` CLI;
- `dist/modes/interactive/interactive-mode.js`: the interactive shutdown change
  for SDK embedders.

Modified runtime members omit stale source-map references. All 1,238 other
upstream members, including the original source maps, remain byte-identical.
The missing upstream license is added. `build-provenance-grios.3.json` records
the source pins and each member's hashes. No upstream lifecycle script ran
during construction.

The reproducible builder and the behavioral regression tests live in the
consuming application's repository, which pins the matching builder and tests
by commit. Both source archives and every edited member body are pinned by
integrity hash; each edit must match exactly one method, and any drift fails the
build. The patch script's member sha256 values equal `shutdownPatch.members` in
the provenance file.

The regression tests run the installed archive in a real pseudo-terminal, both
through the SDK's `InteractiveMode` and through the packaged `pi` CLI, with a
failing shutdown handler. On grios.2, SIGTERM and SIGHUP exited with the
terminal still raw and the session not disposed. On grios.3, every case
(SIGTERM, SIGHUP, Ctrl+D, `/quit`, Ctrl+C twice) ends as follows:

- exit 1;
- the kernel terminal flags show canonical input and echo restored;
- the last cursor-visibility sequence written shows the cursor;
- a session-resource cleanup registered by the test extension, the last step of
  `session.dispose()`, ran exactly once;
- the failure is reported.

The same paths with succeeding handlers still exit 0. In-process tests also
show that nothing the runtime already started runs twice: not when its UI reset
throws part way, not when a session-resource cleanup throws inside
`session.dispose()`, and not when an embedder's dispose wrapper rejects after a
complete teardown. A replacement session that a concurrent `newSession()`
installed while the failing quit handler waited is torn down exactly once.

Use the raw GitHub URL at the full immutable commit containing the archive.

```text
SHA256: af2b5b78ee673c343dd9e4fc5572b11929a53f299d1aeeac07fbb1869cc94d9e
SRI: sha512-pJygG4oKxtKaR8SA6McMHbM7DLznnNU7qBpq7+lEwIGll8U9uIfjZKNDrjJOwjR15nha1DsNUCtf1hO5kiocpg==
```

### Residual behavior (as upstream)

- A shutdown handler that never settles blocks shutdown.
- An unrelated uncaught exception during a signal shutdown's cleanup exits 1
  immediately, without restoring the terminal (upstream crash handler).
- Errors thrown by the terminal-restore operations or by the resume-hint write
  keep upstream handling.
- RPC mode reports a failed quit cleanup as an error response without disposing
  the session; a later shutdown may exit 0.
- Print mode's finalization rejects without disposing the session; signals
  still exit 129/143.
- Embedders that call `AgentSessionRuntime.dispose()` directly still receive the
  rejection and own their teardown.
- The fatal runtime error exit does not run `shutdown()` and is unchanged.
- An extension disposer that throws during the runtime's own UI reset skips the
  rest of that reset, as upstream does; the session is still disposed and the
  terminal restored.
- Session lifecycle transitions are not serialized. A `/new`, `/resume`, `/fork`
  or import still in flight when quit or a signal arrives can tear the outgoing
  session down twice. It can also install a replacement after the fallback
  decision, which is not disposed before exit. Upstream has the same race on a
  successful quit, with or without this change.

## grios.2 (superseded)

grios.2 changed four members (package identity, shrinkwrap metadata and both
dispatchers). Its interactive quit and signal shutdown issue is described above
and fixed in grios.3. The archive and `build-provenance-grios.2.json` remain
unchanged.

```text
SHA256: f5a43cd78991e3eab7e5e8e2d56fa435855b2a30991db295f3e7073bcd53866a
SRI: sha512-LDqye+u85xVLZscf6mGrRYZ1DHaA2M1d2EPlgdqfPR2JWzuc6w9kfeuKfk6njxMXuYCmbeaJlLHf1q7Ux3A6Kg==
```

The original grios.1 artifact and its provenance remain unchanged.
None of the derivatives has been published to the npm registry.
