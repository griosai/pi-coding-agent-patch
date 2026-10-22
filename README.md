# Pi Coding Agent Security Patch

STATUS: REVIEWED_DEPENDENCY_ARCHIVE (grios.1); LOCAL_CANDIDATE (grios.3, supersedes grios.2); RELEASE_CANDIDATE (1.3.0-grios.1)
SUMMARY: Unofficial derivatives of @earendil-works/pi-coding-agent 1.0.0 and 1.3.0. grios.1 is metadata-only (shrinkwrapped brace-expansion fix; all upstream runtime files byte-for-byte). grios.2 and grios.3 keep that fix and change runtime members for session_shutdown failure handling; see SHUTDOWN-PATCH.md for their behavior, checksums and residuals.

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

## 1.3.0-grios.1

`griosai-pi-coding-agent-1.3.0-grios.1.tgz` identifies itself as
`@griosai/pi-coding-agent@1.3.0-grios.1`. It is built from the official
`@earendil-works/pi-coding-agent@1.3.0` archive. It changes the package
identity in `package.json` and re-applies the grios.3 session_shutdown fix to
three runtime members (`dist/core/extensions/runner.js`,
`dist/bundle/chunks/chunk-66G7ITPS.js`,
`dist/modes/interactive/interactive-mode.js`; see SHUTDOWN-PATCH.md for the
behavior). Upstream 1.3.0 already resolves `brace-expansion` 5.0.12, so no
dependency change is needed. 1,272 of 1,276 original members are unchanged; the modified members
omit stale sourceMappingURL references. The original upstream MIT license is
included. No upstream lifecycle script was run while building the archive.
`build-provenance-1.3.0-grios.1.json` records each member's source and resulting
hash and the official source archive.

Pin the raw GitHub URL at the full immutable commit containing the archive,
never a branch URL. Preserve these checksums in the consumer lock:

```text
SHA256: 47f6baf77d5890287fa313d004261b01a2847f1c9de74de2b7ffd1a79cb8631b
SRI: sha512-36FMhJfmOwDlM9K9JBNCxg3GbRBnIWYjKQHoweE/k116N03sIX2ru86tRVgKMmis/o5/YkvPZ9rEI7gWHRGKlg==
```

Original package: https://registry.npmjs.org/@earendil-works/pi-coding-agent/-/pi-coding-agent-1.3.0.tgz

License source: https://raw.githubusercontent.com/earendil-works/pi/71023aec1546d6d677a65669c5665c0927ce0dd0/LICENSE
(SHA256 0457f5bcec3b3b211605dfb5d1a49042fd638f3686a410fe099c24a25af13c48)
