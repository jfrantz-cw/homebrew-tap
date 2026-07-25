# jfrantz-cw/homebrew-tap

Homebrew formulae for [Overmind](https://github.com/jfrantz-cw/overmind), a local
control plane for Claude Code and Codex sessions in one terminal UI.

```bash
brew install jfrantz-cw/tap/ovm
```

The command is `ovm`, not `overmind`. An unrelated Procfile process manager
already owns `overmind` in homebrew-core, and sharing the name would collide on
`PATH`.

The formula installs the prebuilt release archive, so no Rust toolchain is
needed, and Homebrew's download path leaves no `com.apple.quarantine` attribute,
so macOS runs it without the `xattr -d` step a manual tarball download requires.

## How this stays current

`Formula/ovm.rb` is generated, not hand-edited. The `Sync formula` workflow runs
hourly, reads the latest release from the overmind repository, and regenerates
the formula with `scripts/update-homebrew-formula.sh` from that release's tag, so
there is one generator and checksums always come from the release's own
`SHA256SUMS`.

The sync is pull-based so this repository updates itself with the built-in
`GITHUB_TOKEN` and holds no long-lived credential. Releases can therefore lead
the formula by up to an hour; run the workflow manually to close the gap.
