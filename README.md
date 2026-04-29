# aozora-epub

> ⚠️ **Parked repository.** This project is intentionally minimal —
> see [ADR-0001](./docs/adr/0001-parked-until-differentiation.md) for
> why. The scaffolding is here so future work can start immediately;
> there is no real implementation yet.

EPUB3 generator for [Aozora Bunko (青空文庫)
notation](https://www.aozora.gr.jp/annotation/). When activated, this
will take `.txt` files in canonical aozora format (Shift_JIS or UTF-8)
and produce a spec-compliant **EPUB 3.3** package suitable for any
current reading system — Apple Books, Kobo, Calibre, Vivliostyle,
Thorium.

## Why parked

The aozora→EPUB3 conversion space is mature and contested. Existing
tools — `hmdev/AozoraEpub3` (de-facto standard), `whiteleaf7` fork,
`急急如律令` (kyukyunyorituryo) electronic-publishing-grade fork — already
cover this need well. ADR-0001 records the parking decision and lists
the differentiation axes that would need to materialise before
serious work begins (electronic-publishing-grade `miette`
diagnostics, 17 k-corpus regression sweep à la afm ADR-0007,
Docker-only reproducibility, EPUB-spec test corpus, etc.).

## Sibling projects

| Repo | Role |
|---|---|
| [`P4suta/aozora`](https://github.com/P4suta/aozora) | Aozora Bunko notation parser |
| [`P4suta/aozora-tools`](https://github.com/P4suta/aozora-tools) | Editor tooling |
| [`P4suta/aozora-hugo`](https://github.com/P4suta/aozora-hugo) | Hugo module |
| [`P4suta/aozora-zola`](https://github.com/P4suta/aozora-zola) | Zola theme |
| [`P4suta/aozora-obsidian`](https://github.com/P4suta/aozora-obsidian) | Obsidian plugin |
| [`P4suta/aozora-logseq`](https://github.com/P4suta/aozora-logseq) | Logseq plugin |
| [`P4suta/aozora-pandoc`](https://github.com/P4suta/aozora-pandoc) | Pandoc Lua filter |
| [`P4suta/aozora-typst`](https://github.com/P4suta/aozora-typst) | Typst package |
| **`P4suta/aozora-epub`** (this repo) | **EPUB3 generator (parked)** |
| [`P4suta/afm`](https://github.com/P4suta/afm) | Markdown dialect on top of aozora |

## Licence

Dual-licensed under [Apache-2.0](./LICENSE-APACHE) OR [MIT](./LICENSE-MIT).
See [`NOTICE`](./NOTICE) for third-party material and the
acknowledgement of the AozoraEpub3 family as prior art.
