# Pi Coding Agent Security Patch

STATUS: REVIEWED_DEPENDENCY_ARCHIVE
SUMMARY: Unofficial, metadata-only derivatives of @earendil-works/pi-coding-agent 1.0.0 repair shrinkwrapped brace-expansion and Undici dependencies. All upstream runtime files and assets are preserved byte-for-byte.

## Undici repair: 1.0.0-grios.4

`griosai-pi-coding-agent-1.0.0-grios.4.tgz` identifies itself as
`@griosai/pi-coding-agent@1.0.0-grios.4`. It derives from the `.1` archive below,
at immutable source commit `4ed796304ff951d50376bcbb4667e44dc094af13`. The
version `1.0.0-grios.3` already names a different derivative on this
repository's `codex/pi-1.0.0-grios.3` branch, so this repair uses `.4` and does
not include that derivative's changes.

Only `package/package.json` and `package/npm-shrinkwrap.json` change: the
derivative version becomes `.4`, and Undici's manifest/shrinkwrap dependency
changes from `8.10.2` to official `8.12.2`, with its matching registry URL and
integrity. Undici's recorded engines (`node >=22.19.0`) and MIT license already
match `8.12.2`. The existing `brace-expansion@5.0.12` repair remains unchanged.

The archive contains 1,244 unique regular members, 7,473,068 compressed bytes
and 22,717,587 member payload bytes. The other 1,242 raw archive members,
including their modes and the original MIT license, are unchanged from `.1`.
The gzip header names no build host (OS byte 255, "unknown").
`build-provenance-1.0.0-grios.4.json` records the source, dependency tuple, each
member's before/after hash, the uncompressed tar SHA-256 and the Node/zlib
toolchain. The uncompressed tar hash is the platform-independent content pin;
the compressed bytes below also depend on Node's bundled zlib.

The canonical builder (`scripts/build-patched-pi-package.mjs --recipe grios.4`
in the Grios control plane) reproduces this archive byte-for-byte from `.1`, and
a separate derivation from the earlier reviewed Undici candidate produced the
same bytes. Independent archive review confirmed exactly eight JSON value
changes across the two metadata members. No upstream code or lifecycle script
was executed while constructing or inspecting this archive.

```text
SHA256: a242bb7ef2cec8e5941cbe3771be3416fd4f9845cb42e1a94765d351d49b5981
SRI: sha512-MTpA6pSffeghVQb9oOWZfutuvlL7zZsF82g65KygQv0inLPnOk3DotAofb26/x+vYV5DBuEv84kQZVH6hnIVYA==
Tar SHA256: dab55544864127bd235534faf376fd5b287fa604dfbecfffd97fd0264593b44a
```

An isolated consumer resolved this exact archive with `--package-lock-only`
and `--ignore-scripts`; its production lock-only audit reported zero findings.
That proof does not install the package or inspect installed payloads. Fresh
installation, repeat `npm ci --ignore-scripts`, installed-payload inspection and
installed-tree auditing remain required before claiming consumer acceptance.
Use the raw GitHub URL at the full immutable commit containing `.4`, never a
branch URL, and retain its exact integrity in the consumer lock.

## Original brace-expansion repair: 1.0.0-grios.1

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
