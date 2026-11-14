# Pi Coding Agent Security Patch

STATUS: HISTORICAL PUBLISHED DERIVATIVES; LOCAL 1.5.2-grios.2 CANDIDATE
SUMMARY: Unofficial derivatives of @earendil-works/pi-coding-agent 1.0.0, 1.3.0, 1.5.0 and 1.5.2. The unpublished 1.5.2-grios.2 candidate adds canonical session durability and queued-input observation to the published 1.5.2-grios.1 predecessor. Older sections retain their historical build-time status; no candidate is an npm release or installed Grios runtime.

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

## 1.5.0-grios.1

`griosai-pi-coding-agent-1.5.0-grios.1.tgz` identifies itself as
`@griosai/pi-coding-agent@1.5.0-grios.1`. It is built from the official
`@earendil-works/pi-coding-agent@1.5.0` archive (source commit
`f9a26365568127461c47a07a37dcb42c140a3ac5`, bound by the registry's SLSA
provenance). It changes the package identity in `package.json` and re-applies
the same session_shutdown fix, unchanged, to three runtime members
(`dist/core/extensions/runner.js`, `dist/bundle/chunks/chunk-44DLKSKE.js`,
`dist/modes/interactive/interactive-mode.js`; see SHUTDOWN-PATCH.md). Upstream
1.5.0 still resolves `brace-expansion` 5.0.12. 1,282 of 1,286 original members
are unchanged; the modified members omit stale sourceMappingURL references.
The original upstream MIT license is included. No upstream lifecycle script was
run while building the archive, and rebuilding reproduces the same bytes.
`build-provenance-1.5.0-grios.1.json` records each member's source and
resulting hash and the official source archive.

Pin the raw GitHub URL at the full immutable commit containing the archive,
never a branch URL. Preserve these checksums in the consumer lock:

```text
SHA256: cd932f41ea83d105ffb85ed6be02777b3453cf68f9e8ca870ec383bd38225c86
SRI: sha512-lKhDs7h8X0WhT17KZpYTodVBTJri/c7tMtVkIWEFalkm8lCN9al5164eOaje9PLozFDuWQlPMGPBRRGdAxKGnA==
```

Original package: https://registry.npmjs.org/@earendil-works/pi-coding-agent/-/pi-coding-agent-1.5.0.tgz

License source: https://raw.githubusercontent.com/earendil-works/pi/f9a26365568127461c47a07a37dcb42c140a3ac5/LICENSE
(SHA256 0457f5bcec3b3b211605dfb5d1a49042fd638f3686a410fe099c24a25af13c48)


## 1.5.2-grios.1 (local candidate)

SUMMARY: Re-applies shutdown and idle-editor dispatch changes to the official Pi 1.5.2 archive and preserves canonical credential settlement after a preceding disposal failure; no upstream lifecycle scripts execute. The derivative remains unpublished until review and an authorized branch push.

Source commit: `b4afdddf44e059c67ccf5097e5317d913521b470` (registry provenance-bound).
Artifact SHA256: `0eba02a5a7b57cdbaea083e9b8ec903eb2eab8e99e8e03d248842b27cc03d0b9`.
SRI: `sha512-N7hYErSRC2/wVNhAuJmDGFSIc2OYik6kgq23w79dYyVugTUGSVwAmtAIFi3UsmN6z6GYVEWY3InLXdRPyFaLTg==`.

The six changed upstream members are package identity metadata, canonical agent-session runtime disposal, extension runner, the matching CLI bundle chunk, interactive mode, and its editor callback declaration. The original MIT license is added. The other 1,318 upstream members remain byte-for-byte, including original source maps; modified members omit stale sourceMappingURL references. The upstream manifest pins brace-expansion 5.0.12 and is retained unchanged; this archive has no npm-shrinkwrap.json, and the consumer lock records the resolution. `build-provenance-1.5.2-grios.1.json` records every member hash and the official source archive. Two independent builds produced identical bytes. The consumer's `docs/pi-fork-delta.md` documents every original patch hunk and upgrade checks.

## 1.5.2-grios.2 (unpublished candidate)

SUMMARY: Extends the shutdown/credential-settlement predecessor with opt-in canonical session durability, exact queued-input custody and detached per-request ancestry. Its production URL and consumer admission are pending independent review and publication. No upstream lifecycle script or downloaded source was executed by the artifact builder.

Source: official Pi 1.5.2, commit `b4afdddf44e059c67ccf5097e5317d913521b470`.
Artifact: `griosai-pi-coding-agent-1.5.2-grios.2.tgz`.
SHA256: `715556e05ac72ef6bbb8c85d7fae672a92feacf694da8393e1aada07da7526f2`.
SRI: `sha512-DVJie+ZYsK4KEl0Pcz0SW1IitIgSmmzMmJ6y0GwOgV5VQAtbdy4E76BN5PmV0tBiDOpri3c2mjJAOVdO90BzvQ==`.

`build-provenance-1.5.2-grios.2.json` records source integrity, exact owned transforms and every resulting member hash. Fourteen original members change; 1,309 original raw archive members remain identical. The added pinned upstream license produces 1,325 files. Two independent builder runs produce identical archive and provenance bytes. Public declarations match the native implementation and bundled CLI spans.

The canonical journal remains the sole durable owner. Native queues retain exact input identity through cancellation, restoration and dispatch. Matching raw recovery preserves an executing input handler's exclusive claim and advances other inputs. Replacement and prepared restoration permanently revoke the old start; processed content remains in the same native record for one later delivery without rerunning its input hook. Request observation changes no credential, provider, billing or tool authority. Accepted but undelivered queued inputs have no crash-recovery delivery guarantee; missing observation remains unknown.

Local qualification includes 92 focused observation controls per module/bundle format and 56 top-level package-builder, native-wrapper and lifecycle checks. The wrapper includes the broader storage/recovery/poison controls. Grios consumers are qualified separately; neither fixture checks nor this archive establish installed acceptance. Some later boundary controls are retrospective sensitivity checks, explicitly identified in the consumer's repair report. The consumer's `docs/pi-fork-delta.md` documents native owners, provenance, prior failed reviews and remaining production steps.

Use a full immutable commit URL only after that exact archive is published and downloaded bytes are verified. A local source commit, branch URL or existing grios.1 pin does not qualify this candidate for production admission.
