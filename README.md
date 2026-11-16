# wordcraft-web-safe

An audited, re-hosted mirror of [storytold/wordcraft](https://github.com/storytold/wordcraft)'s
`wordcraft-web` release build, used by VARKIS's Office Studio instead of
fetching it from storytold's infrastructure at runtime.

The [v0.5.0 release](https://github.com/ASDK-Systems/wordcraft-web-safe/releases/tag/v0.5.0)
carries `wordcraft-web-0.5.0.zip`, a byte-for-byte mirror of upstream's own
release asset — re-downloaded and SHA-256-verified against the original
after uploading, and VARKIS's own download code (`server/craftAppBinaries.ts`)
verified end-to-end against this fork before `server/craftApps.ts` was
repointed here.

See [AUDIT.md](AUDIT.md) for what was checked before mirroring it (short
version: it makes no outbound network calls, so nothing was changed — this
is an unmodified copy, not a modified derivative work).

Licensed under either of [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE)
at your option, same as upstream.

Native WordCraft binaries are **not** mirrored here — VARKIS downloads those
directly from storytold's own releases, verified against the same pinned
SHA-256 hashes either way.
