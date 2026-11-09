STATUS: REVIEWED_DEPENDENCY_ARCHIVE
SUMMARY: Pi Coding Agent 1.0.4 with an explicit derivative identity and the original MIT license; all upstream runtime and asset bytes are retained.

The archive identifies itself as `@griosai/pi-coding-agent@1.0.4-grios.1`.
Only the `name` and `version` fields in `package.json` change; the original MIT
`LICENSE` is added. Upstream 1.0.4 already pins `brace-expansion` to 5.0.12 and
ships no shrinkwrap, so this derivative changes no dependency or runtime code.

Of 1,248 upstream members, 1,247 remain byte-for-byte identical, including their
tar headers and modes. The archive contains 1,249 members. The adjacent
`build-provenance-1.0.4.json` records every original and output member hash.
Its `published: false` field records the build-time state, before any hosting.
No upstream lifecycle script ran during construction.

Use a raw GitHub URL pinned to the full immutable commit containing this file.
This is an archive for dependency installation, not an npm registry publication
or a Grios application release.

```text
SHA256: c2f6dd7a7d6a7946707d4d6edd97079210635e0f2b8ea863cee5e6d5524048a8
SRI: sha512-cfXLYWVGLpwuY0PsxEKI2a5psEbvgtZm85DezJPZiHoav0wli73m4y3tj8TusA3FAMXlR6NWIOR5KGCHFtLY1Q==
```

Source: https://registry.npmjs.org/@earendil-works/pi-coding-agent/-/pi-coding-agent-1.0.4.tgz

License: https://raw.githubusercontent.com/earendil-works/pi/7c10bd4337495ee613f2224843ecdf349b80d1df/LICENSE

Builder: `scripts/build-patched-pi-package-104.mjs` in `griosai/grios-control-plane`,
SHA256 `38565e28346daaf44a5a255eb55ff4e0001847861bf6626a3d321f7c04a439ca`.
It reuses the unchanged bounded archive parser from the historical builder.
Earlier derivative archives and their provenance remain unchanged.
