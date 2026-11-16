# wordcraft-web-safe

An audited, re-hosted mirror of [storytold/wordcraft](https://github.com/storytold/wordcraft)'s
`wordcraft-web` release build, used by VARKIS's Office Studio instead of
fetching it from storytold's infrastructure at runtime.

See [AUDIT.md](AUDIT.md) for what was checked and found before this build was
mirrored here (short version: it makes no outbound network calls, so nothing
was changed - this is an unmodified copy of upstream's own release asset).

Licensed under either of [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE)
at your option, same as upstream.

Native WordCraft binaries are **not** mirrored here - VARKIS downloads those
directly from storytold's own releases, verified against the same pinned
SHA-256 hashes either way.
