# barenoc-downloads

**Public installer downloads for BareNOC Desktop / BareNOC Connect.** Binaries only — all source
lives in the private `BareNOC-Desktop` repo.

## Why a separate repo
Public downloads need a **public** host. GitHub Releases on a private repo require authentication,
so built installers are published here as Releases while the source stays private.

## Verify what you download
Every release ships a `.sha256` file next to the installer. Always check it:

```bash
sha256sum BareNOC-Desktop-0.1.0.msi
# compare with the .sha256 asset of the SAME release
```

**Builds are not reproducible** — a rebuild of identical source produces different bytes. Verify
against the hash published *with the release you downloaded* (or the `downloads/…/versions.json`
manifest), never a hash copied from another build or a chat message.

## Layout
- **GitHub Releases** — the installer files (MSI / RPM) + `.sha256` + notes.
- `downloads/barenoc-desktop/versions.json` — the machine-readable manifest the website and the
  app's updater consume (version, urls, sha256, size, minimum app version).

## Interim status
This repo is the interim host. The target state is Cloudflare R2 + `downloads.barenoc.com`
(zero-egress CDN) with this repo (or R2) serving the artifacts; the manifest URL will be the only
thing that changes for consumers.
