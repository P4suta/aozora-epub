## Summary

<!-- One or two sentences: what this PR changes and why. -->

## Type of change

- [ ] Bug fix
- [ ] New feature
- [ ] Refactor (no behaviour change)
- [ ] Documentation / ADR
- [ ] CI / developer tooling
- [ ] `aozora` parser pin bump

## Unparking PR?

- [ ] **This PR unparks the project.**

If the box above is checked, the PR description **must**:

1. Update or supersede [ADR-0001](../docs/adr/0001-parked-until-differentiation.md)
   with a concrete activation criterion that triggered the unpark
   (one of the three listed in ADR-0001, or a new criterion documented
   in a successor ADR).
2. Reference the specific incident, differentiation axis becoming a
   real priority, or downstream sibling need that justifies activation.
3. Adjust `version` away from `0.0.0` only as part of the unparking
   sequence — not before.

Until activation criteria are met, ADR-0001 stands and PRs that add
functionality should be closed in favour of contributing to
[`hmdev/AozoraEpub3`](https://github.com/hmdev/AozoraEpub3),
[`whiteleaf7/AozoraEpub3`](https://github.com/whiteleaf7/AozoraEpub3),
or [`kyukyunyorituryo`'s Improved AozoraEpub3](https://kyukyunyorituryo.github.io/aozoraepub/).

## Checklist

- [ ] `cargo test --workspace --all-targets` passes locally.
- [ ] `cargo clippy --workspace --all-targets --all-features -- -D warnings` is clean.
- [ ] `cargo fmt --all -- --check` passes (lefthook pre-commit reformats automatically).
- [ ] `cargo doc --workspace --no-deps --document-private-items` builds with `RUSTDOCFLAGS=-D warnings`.
- [ ] Updated `CHANGELOG.md` under `[Unreleased]` (or stated why it doesn't need a changelog entry).
- [ ] Commit messages follow Conventional Commits (commit-msg hook enforces).

## How to test

<!-- Reviewer-facing repro steps. -->
