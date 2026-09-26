# Repository instructions

This Go project has a CLI in `cmd/downloader/`, a Fyne GUI in `cmd/gui/`, reusable downloading/parsing code in `pkg/`, and development notes in `docs/dev.md`. Read `CONTRIBUTING.md` and the affected site's tests before changing parsing or output formats.

Use the current `go.mod`: Go 1.23 with toolchain go1.24.4; the Travis Go 1.22 declaration is older and does not override the module. `go mod download` resolves dependencies. Build the CLI with `go build -o comics-downloader ./cmd/downloader`; the GUI also needs Fyne's native graphics/toolchain prerequisites (the Travis Linux setup installs GL/X11 development libraries). Cross-platform Makefile targets require their own environment; do not infer architecture correctness from a target name alone.

Run focused `go test ./pkg/<affected-package>` checks and `go test ./...` when the change warrants the full suite and native prerequisites exist. Inspect test network usage first: site tests may depend on external content. Prefer saved HTML fixtures for parser regressions; use only authorized URLs/content and a disposable output directory for real download checks. Daemon mode repeatedly downloads and is not a smoke test.

For prose-only work, verify links/commands and run `git diff --check -- <changed-paths>`. Distinguish CLI build, GUI build, fixture tests, and live-site compatibility; a stale supported-sites list is not current service evidence.

Complete the authorized change through relevant verification and repair of introduced failures. Resolve routine implementation choices directly; ask only for information or decisions that materially affect the result. If blocked, name the affected action and missing prerequisite, continue independent work, and close with changed paths, checks actually run, and unverified behavior.
