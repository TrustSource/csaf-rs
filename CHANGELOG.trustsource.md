# Changelog of the TrustSource fork

Changes of `TrustSource/csaf-rs` compared to upstream [`csaf-rs/csaf`](https://github.com/csaf-rs/csaf). The format follows
[Keep a Changelog](https://keepachangelog.com/), the versions follow [Semantic Versioning](https://semver.org/): the upstream
version plus the build metadata `+ts.N` of this fork. Use the fork as a git dependency pinned to a tag, e.g.
`csaf-rs = { git = "https://github.com/TrustSource/csaf-rs", tag = "v0.7.3+ts.1" }`.

## [0.7.3+ts.1] - 2026-11-24

Based on upstream `main` at 780bb3f (v0.7.3 plus 11 commits).

### Added
- Test 6.1.60.3 (Extension Metadata) for CSAF 2.1.
- `csaf::extension_registry`: offline registry of extension schemas and extension metadata, filled by the integrator before
  validation (`register_extension_schema`, `register_extension_metadata`, `register_extensions_from_dir`). Extensions are
  never fetched from the network.
- `csaf validate --extension-dir <DIR>` and environment variable `CSAF_EXTENSION_DIR` to register extensions from a directory.
- Supplementary test cases for 6.1.50, 6.1.60.2, 6.1.60.3 and 6.1.64.12 (a corrected version of OASIS case 6-1-64-12-13).

### Changed
- 6.1.50: `vers:all/*` is valid; `vers:all` with other constraints is an error; for other unsupported VERS types the warning names
  the type and the constraints are checked best effort (upstream PR csaf-rs/csaf#1530).
- 6.1.60.2: extensions are validated against their registered extension schema. Unregistered extensions still result in a warning,
  which now includes `$schema` and the extension category.

### Notes
- OASIS case 6-1-64-12-13 is listed as valid but is invalid itself (oasis-tcs/csaf#1757); csaf-rs reports it correctly.
