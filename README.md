# dna_guides

The DNA layer that defines how guides and documentation are written.

## Content

- `dna/doc/en/guides/dna-guides-guide.md` — how to add a new guide to a
  DNA
- `dna/doc/en/guides/doc-guide.md` — the writing style for guides

## Usage

Declare it as a dev-dependency and initialize once:

```bash
pnpm add -D @tssuite/dna-guides   # TypeScript projects
dart pub add dev:dna_guides    # Dart projects
helix init
```

The placed test instantiates and verifies the DNA on every test run. This
layer sits on top of
[dna_base](https://github.com/ggsuite/dna_base) — everything generic comes
from there, this repo only adds its own topic.

## Development

This repo has `role: "dna"` in `dna/_dna.json`: the `dna/` folder is
authored by hand, never generated. The repo instantiates its own DNA — run
`dart test` after changes; commit first (a file the DNA would overwrite
must not carry uncommitted work).
