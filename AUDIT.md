# Audit record: wordcraft-web v0.5.0

This repo mirrors the `wordcraft-web-0.5.0.zip` release asset from
[storytold/wordcraft](https://github.com/storytold/wordcraft) v0.5.0, so VARKIS
never fetches that build from storytold's infrastructure at runtime.

## What was checked

The wasm-bindgen glue JS (the only place code running in this build can reach
the network from, since the compiled `.wasm` can only call out through an
imported JS function) was searched for every outbound-network-capable API:
`fetch`, `XMLHttpRequest`, `WebSocket`, `sendBeacon`, `EventSource`,
`window.open`, `.src =` / `new Image`, `location` reassignment
(`location =`, `.href =`, `.assign`, `.replace`, `top.location`),
`importScripts`, and any external `<script>`/`<link>` URL in `index.html`.

The compiled `.wasm` binary's raw string table was also scanned for any URL.

## What was found

- Exactly one `fetch()` call: the glue's own same-origin load of its paired
  `.wasm` file. Required, benign.
- One `.src =` binding, traced to a WebGPU rendering import
  (`__wbg_set_src_...`, clustered with other `GPU*` property bindings used by
  the wgpu rendering backend) - not a DOM content element, not reachable from
  document content.
- No `XMLHttpRequest`, `WebSocket`, `sendBeacon`, `EventSource`,
  `window.open`, `importScripts`, or `location` reassignment anywhere in the
  glue.
- `index.html` references only its own two local files (the glue `.js` and
  the `.wasm`), nothing external.
- The `.wasm` binary's string table contains only OOXML/XML namespace
  constants (never fetched - they're plain string comparisons used when
  reading/writing `.docx` XML) and a handful of static about-box/credit
  links (the project's own GitHub repo, its Discord, its website, a few
  upstream `wgpu`/`egui` issue-tracker URLs, and `zotero.org`). None of these
  appear anywhere in the glue JS as an actual network call - the "Zotero"
  menu item visible in the app's UI is inert in this build, since real
  Zotero integration would need a live network/local-service call that
  simply isn't wired to anything reachable here.

## Conclusion

This release makes no outbound network calls. Nothing was patched or
stripped - the file in this repo's release is a byte-for-byte, unmodified
mirror of upstream's own release asset, not a modified derivative work.
