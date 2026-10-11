# Pi Coding Agent Security Patch

STATUS: REVIEWED_DEPENDENCY_ARCHIVE (grios.1); LOCAL_CANDIDATE (grios.3, supersedes grios.2)
SUMMARY: Unofficial derivatives of @earendil-works/pi-coding-agent 1.0.0. grios.1 is metadata-only (shrinkwrapped brace-expansion fix; all upstream runtime files byte-for-byte). grios.2 and grios.3 keep that fix and change runtime members for session_shutdown failure handling; see SHUTDOWN-PATCH.md for their behavior, checksums and residuals.

The sections below describe grios.1. The grios.3 archive
(`griosai-pi-coding-agent-1.0.0-grios.3.tgz`, provenance in
`build-provenance-grios.3.json`) and the superseded grios.2 archive are
documented in `SHUTDOWN-PATCH.md`.

The archive identifies itself as `@griosai/pi-coding-agent@1.0.0-grios.1`.
It changes the package identity in `package.json` and `npm-shrinkwrap.json`,
and replaces the shrinkwrapped `brace-expansion@5.0.9` resolution with the
official `5.0.12` version, URL and integrity. It includes the original upstream
MIT license omitted from the npm archive. No upstream lifecycle script was run
while constructing the archive.

The 1,241 original nonmetadata members are unchanged. The complete archive has
1,244 members. `build-provenance.json` records each member's source and resulting
hash, the official source archive, and the exact dependency change. Its
`published: false` field describes the build-time state, before GitHub hosting;
the derivative has not been published to the npm registry.

Use the raw GitHub URL at the full immutable commit containing the archive,
never a branch URL. Preserve these exact archive checksums in the consumer lock:

```text
SHA256: 358f54f65626bd612b0b2b09f38f1c511eaa423e98976bd7c5b2ed65511966c2
SRI: sha512-vrqCbFZq8u9HPxG7fGoOnMjBGBBIlLXc2cO/vFoRIxwWlQPWY4590cvn24U7obhgWXxymF+AA6rf86ckh0Je+A==
```

Upstream: https://github.com/earendil-works/pi

Original package: https://registry.npmjs.org/@earendil-works/pi-coding-agent/-/pi-coding-agent-1.0.0.tgz

License source: https://raw.githubusercontent.com/earendil-works/pi/a13d35a742c6ef8462812a28fbe1d8c8b7431c32/LICENSE

This repository distributes only the dependency patch and provenance. It does
not contain or publish the Grios application.
