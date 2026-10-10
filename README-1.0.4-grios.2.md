STATUS: LOCAL_DEPENDENCY_CANDIDATE_UNPUBLISHED
SUMMARY: Pi Coding Agent 1.0.4 with the existing SDK and bundled CLI shutdown failure contract restored; independent review and exact publication approval remain required.

This separate archive identifies itself as `@griosai/pi-coding-agent@1.0.4-grios.2`.
It preserves every registered shutdown cleanup handler and rethrows the first
failure, including primitive failures, after cleanup completes. Diagnostic
failures cannot interrupt the remaining handlers. Non-shutdown dispatch is
unchanged. The same existing transformation covers the SDK extension runner and
its bundled CLI counterpart; no Grios host wrapper is required.

Of 1,248 original upstream members, 1,245 preserve their original bytes and headers.
Only package identity and the two pinned runtime members change; the pinned MIT
LICENSE is added. Modified runtime members omit stale sourceMappingURL references.
Existing dependency specifications, including brace-expansion 5.0.12, stay intact.
The adjacent provenance records every original/output member digest. Its
published:false is the immutable build-time state. No upstream lifecycle script
was executed while building the archive.

The unmodified 12-case real SDK test file has 10 failures against 1.0.4-grios.1
and 12 passes against this candidate, including all nine unwrapped failure cases.
Both runs use one physically copied dependency closure. An initial candidate
fixture omitted nested dependencies and executed zero tests; its misleading
summary was explicitly invalidated and excluded. The corrected run checks exit 0,
12 executed/passed cases, zero failed suites and identical test names. This is
offline SDK evidence, not application installation or provider acceptance.

This artifact is intended for a full-commit-pinned raw GitHub dependency URL.
It is not an npm publication or application release. Earlier archives, their
README files and provenance remain unchanged.

```text
Archive bytes: 7488855
SHA256: 43b100be73a9458e86ede969def4986e2b1d2a5dd0f9d8d76336f28edf81426c
SRI: sha512-oxnPz0P0M8TABdTcD54SIAGRR7HgFYvkYurUXv+zUXXOc/PBqcDfbrLdsapbCQlulNBNoNaHiM1T+Utw6jXG7w==
```

Source: https://registry.npmjs.org/@earendil-works/pi-coding-agent/-/pi-coding-agent-1.0.4.tgz

License: https://raw.githubusercontent.com/earendil-works/pi/7c10bd4337495ee613f2224843ecdf349b80d1df/LICENSE

Preparation owner: griosai/grios-control-plane scripts/build-patched-pi-package-104.mjs,
SHA256 f3478d2aa7dadbaf87b66200be3dd43bec12d75fa57e50bafe827629d6234d6f.
Single shutdown transformation owner: griosai/grios-harness scripts/pi-shutdown-patch.mjs,
SHA256 a7393b15dc99576a91046d5c94e79b9f1d72effb625e29c56f7113fdb5f821ca.
The builder validates that owner's exact bytes before importing them. The archive
itself has no local checkout or preparation-module path dependency.

next_action: Complete independent review, then obtain approval for the exact
prepared commit before publishing this additional archive.
