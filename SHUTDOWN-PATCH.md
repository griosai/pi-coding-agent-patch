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

The reproducible builder and behavioral regression tests are maintained in
`griosai/grios-harness`: `scripts/build-patched-pi-package.mjs`,
`scripts/pi-shutdown-patch.mjs`, `test/build-patched-pi-package.test.ts`, and
`test/pi-shutdown-patch.test.ts`. Both source archives and member bodies are
integrity-pinned; drift fails the build.

Use the raw GitHub URL at the full immutable commit containing the archive.

```text
SHA256: f5a43cd78991e3eab7e5e8e2d56fa435855b2a30991db295f3e7073bcd53866a
SRI: sha512-LDqye+u85xVLZscf6mGrRYZ1DHaA2M1d2EPlgdqfPR2JWzuc6w9kfeuKfk6njxMXuYCmbeaJlLHf1q7Ux3A6Kg==
```

The original grios.1 artifact and its provenance remain unchanged.
The derivative has not been published to the npm registry.
