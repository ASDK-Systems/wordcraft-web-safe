# wordcraft-web-safe

An audited, re-hosted mirror of [storytold/wordcraft](https://github.com/storytold/wordcraft)'s
`wordcraft-web` release build, used by VARKIS's Office Studio instead of
fetching it from storytold's infrastructure at runtime.

**Status: audit done, release asset not uploaded yet.** AUDIT.md and the
licenses below are in place; the actual `wordcraft-web-0.5.0.zip` file still
needs to be attached to a GitHub Release here (pending binary-upload
tooling). Until it is, VARKIS's own registry (`server/craftApps.ts`) still
points at storytold's release directly for the web build, not here.

See [AUDIT.md](AUDIT.md) for what was checked and found (short version: it
makes no outbound network calls, so nothing was changed — the file that will
be mirrored here is an unmodified copy of upstream's own release asset).

Licensed under either of [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE)
at your option, same as upstream.

Native WordCraft binaries are **not** mirrored here — VARKIS downloads those
directly from storytold's own releases, verified against the same pinned
SHA-256 hashes either way.
