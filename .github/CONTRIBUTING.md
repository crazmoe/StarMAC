# Contributing to StarMAC

Thanks for your interest in improving StarMAC! Issues and pull requests may be written in
English or German.

## Reporting bugs and suggesting features

Please use the [issue forms](https://github.com/crazmoe/StarMAC/issues/new/choose). For bugs,
include the StarMAC version (shown at the bottom of the Settings), the installation method, your
operating system and the STARFACE version. Remove passwords, tokens and other personal data
from logs and screenshots.

Rough ideas and questions are welcome in
[Discussions](https://github.com/crazmoe/StarMAC/discussions), where others can comment and
vote on them; a concrete feature request can then become an issue.

Security problems are reported privately, see [SECURITY.md](SECURITY.md).

## Development setup

Requirements: macOS 13 or later, the Xcode Command Line Tools (`xcode-select --install`),
Rust (stable) and Node 22. Further build tools (e.g. OpenSSL via Homebrew) are listed in
[`.github/workflows/ci.yml`](workflows/ci.yml).

```sh
git clone --recurse-submodules https://github.com/crazmoe/StarMAC.git
cd StarMAC
cargo test --workspace
cd apps/desktop && npm install && npm run tauri dev
```

The layout of the repository is described under "Structure" in the [README](../README.md).

## Before opening a pull request

CI runs the following checks; please run them locally first:

```sh
cargo fmt --all --check
cargo clippy --workspace --all-targets -- -D warnings
cargo test --workspace
cd apps/desktop && npm run check && npm run i18n:check
```

- UI strings go through `t()`, with the German text as the key. Add the translations in
  `apps/desktop/src/lib/i18n/`; `npm run i18n:check` reports missing entries.
- Keep a pull request focused on one change and describe what a user will notice.
- User-visible changes get a line in [`CHANGELOG.md`](../CHANGELOG.md).
- Do not commit credentials, server addresses or recordings from real systems.

## License

By contributing, you agree that your contributions are licensed under the
[MIT License](../LICENSE).

## Code of Conduct

This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md). By taking part you agree
to uphold it.
