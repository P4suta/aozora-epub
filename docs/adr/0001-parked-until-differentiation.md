# 0001. Parked until a clear differentiation axis exists

- Status: accepted (parked)
- Date: 2026-04-29
- Deciders: @P4suta
- Tags: scope, prior-art, parking-lot

## Context

The aozora→EPUB3 conversion space is **mature and contested**. As of
2026-04-29 the well-established alternatives are:

- **[hmdev/AozoraEpub3](https://github.com/hmdev/AozoraEpub3)** —
  the original Java converter, the de-facto standard.
- **[whiteleaf7/AozoraEpub3](https://github.com/whiteleaf7/AozoraEpub3)**
  — fork.
- **[Improved AozoraEpub3 (kyukyunyorituryo / 急急如律令)](https://kyukyunyorituryo.github.io/aozoraepub/)**
  — fork targeting 電書協 EPUB3 制作ガイド compliance, with a
  separate **Android port**.

These tools cover the ordinary path well: they accept aozora `.txt`
(plus zipped image bundles and web-novel HTML in the case of
kyukyunyorituryo), produce EPUB3 that passes epubcheck, and have an
established user base.

A new entrant must answer the obvious question: **why this rather
than AozoraEpub3?**

Plausible differentiation axes (none of which is yet a hard
requirement for this maintainer):

- **Diagnostic quality.** `miette` source-spanned errors when an
  aozora `.txt` has a malformed annotation, instead of "conversion
  failed at line 423". The `aozora` library already exposes spans;
  surfacing them in the converter is the next step.
- **Regression sweep.** Run the converter against the 17 k-work
  Aozora corpus on every CI build (cf. afm ADR-0007) so that no
  release silently breaks any historical fixture.
- **Reproducibility.** Docker-only execution (cf. afm ADR-0002 +
  user `feedback_docker_only_execution`) means a build host with
  Docker produces the exact same EPUB bytes as CI — no JRE drift,
  no font lookup divergence.
- **電書協 EPUB3 制作ガイド compliance as a spec.** Codify the guide
  as machine-checkable rules so the converter both produces compliant
  output and fails loudly when an input would force a violation.
- **First-class library API.** Library crate + thin CLI, so other
  Rust tools (e.g. an aozora-tools editor preview) can re-use the
  pipeline. AozoraEpub3 is harder to embed.

## Decision

**Park the project.** Keep the repository as a minimal scaffold so
that future work can begin immediately without re-bootstrapping. Do
**not** start an implementation race with AozoraEpub3 until at least
one of the differentiation axes above becomes a personal priority.

Concrete parking shape:

- LICENSE files, NOTICE, README explaining the parked status.
- Cargo workspace with one library crate (`aozora-epub`) that is
  empty save for a doc comment pointing at this ADR.
- Workspace `Cargo.toml` carries the eventual dep on the `aozora`
  library, tag-pinned, so the activation step is just "add real
  code".
- No CI workflow, no Dockerfile, no Justfile, no example fixtures —
  these are added when work begins, not before.

## Activation criteria

This ADR will be revised (status: superseded by ADR-XXXX) and the
project unparked when **one of** the following is true:

1. A specific incident or use case where AozoraEpub3 fell short for
   the maintainer (a corner-case the existing converter mishandles
   and won't fix; a workflow constraint Java/Android stack can't
   meet, e.g. self-hosted CI on a no-JRE runner).
2. A clear differentiation axis becomes a real priority — most
   likely `miette`-grade diagnostics combined with the 17 k corpus
   sweep, since both reuse infrastructure already built for `aozora`
   itself.
3. A downstream sibling repo (e.g. `aozora-tools`, `aozora-typst`)
   needs to embed an aozora→EPUB3 path and the existing tools cannot
   be embedded as a library.

## Consequences

Easier:
- **No wasted effort.** We avoid a half-done converter that competes
  with AozoraEpub3 without out-classing it.
- **Clear intent for future readers** (and future me): the parking
  state is a deliberate decision, not stalled work.

Harder:
- **Loss of momentum.** When work begins, the surrounding tooling
  (Docker, CI, Justfile, examples, ADR-0002 / 0003 mirroring afm-epub
  conventions) needs to be added in a single push rather than
  accreted over time.

## Alternatives considered

- **Build aozora-epub now, mirroring afm-epub's full scaffolding.**
  Rejected because we would invest effort against entrenched prior
  art with no clear win condition.
- **Skip the repo entirely; defer creation until work is ready.**
  Rejected because keeping the repo (with this ADR) makes the
  decision discoverable and gives a fixed point for future work.

## References

- AozoraEpub3 (hmdev): <https://github.com/hmdev/AozoraEpub3>
- AozoraEpub3 (whiteleaf7): <https://github.com/whiteleaf7/AozoraEpub3>
- Improved AozoraEpub3 (kyukyunyorituryo / 急急如律令):
  <https://kyukyunyorituryo.github.io/aozoraepub/>
- afm ADR-0007 (corpus sweep philosophy):
  <https://github.com/P4suta/afm/blob/main/docs/adr/0007-MOVED.md>
- 電書協 EPUB3 制作ガイド: <https://ebpaj.jp/counsel/guide>
- aozora repo: <https://github.com/P4suta/aozora>
