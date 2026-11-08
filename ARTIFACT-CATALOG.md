STATUS: CONSOLIDATED_SOURCE_CANDIDATE; RELEASE_AND_CONSUMER_GATES_PENDING
SUMMARY: Nine distinct Pi archives and their provenance are preserved unchanged. Version families are alternatives, not one cumulative upgrade chain. The repository's default remains codex/pi-1.0.0-grios.1; this source candidate does not select or install a consumer version.

## Preserved variants

All filenames begin with `griosai-pi-coding-agent-` and end with `.tgz`.
Each adjacent provenance file pins its compressed SHA256, SHA512 integrity,
package identity and archive members.

| Version | Intended difference | Provenance |
| --- | --- | --- |
| 1.0.0-grios.1 | Original brace-expansion metadata repair | build-provenance.json |
| 1.0.0-grios.2 | Shutdown handler failure propagation; known interactive quit/signal issue | build-provenance-grios.2.json |
| 1.0.0-grios.3 | Later interactive shutdown cleanup repair, with documented residual races | build-provenance-grios.3.json |
| 1.0.0-grios.4 | Undici metadata repair derived from .1; excludes the .2/.3 runtime changes | build-provenance-1.0.0-grios.4.json |
| 1.0.4-grios.1 | Separate upstream1.0.4 identity and license archive | build-provenance-1.0.4.json |
| 1.0.4-grios.2 | SDK and bundled CLI shutdown dispatch failure propagation | build-provenance-1.0.4-grios.2.json |
| 1.3.0-grios.1 | Reapplication of the .3 shutdown repair to upstream1.3 | build-provenance-1.3.0-grios.1.json |
| 1.5.0-grios.1 | Reapplication of the shutdown repair to upstream1.5 | build-provenance-1.5.0-grios.1.json |
| 1.5.0-grios.2 | Preceding shutdown repair plus optional idle editor dispatch callback | build-provenance-1.5.0-grios.2.json |

See [shutdown behavior and residuals](SHUTDOWN-PATCH.md),
[1.0.4 identity notes](README-1.0.4.md),
[1.0.4 dispatch notes](README-1.0.4-grios.2.md), and
[the independent Undici line](README-1.0.0-grios.4.md).
Historical review/test statements in those source documents remain historical;
none substitutes for the selected consumer's current review, tests or install
verification.

## Source lineage

- Canonical base: 4ed796304ff951d50376bcbb4667e44dc094af13.
- Shutdown/1.3/1.5 line: 331f82cdf9215778574199b43298d6cbbf3616c4.
- Existing PR1 and its original caveat history: db1e5717ecb879e7b1570fdda00bdef009b92dc0.
- Separate 1.0.4 line: 099b8b30d7cd89ed07ef3f47e05110578eb1a154.
- Uniquely named Undici derivative: 677842e8c9683ccbc82ff6d5f7c5600761d59da5.

The earlier Undici candidate 86274ba54a0acd5cffe8c67feb3c9f7808ce0c65
uses the already occupied version1.0.0-grios.3 for a different payload. It is
preserved as a parked source alternative and is not the `.3` archive here.
Three earlier unreachable shutdown iterations are also preserved by their
original OIDs, outside this distributable tree. They are not silently assigned
the final `.3` identity.

## Remaining gates

The consolidation preserves artifacts without rebuilding or executing their
vendor code. Read-only archive/provenance checks establish byte and member
identity; they do not establish behavior. Complete fresh independent review,
the selected consumer's affected checks and the current-main release gate
before normal publication/merge. Consumer installation and activation require
their own verified operation. No npm publication or application release is
implied by this source tree.
