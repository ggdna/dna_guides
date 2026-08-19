# dna_guides

The DNA layer that says how guides and documentation are written.

## Guides

- `dna/doc/guides/dna-guides-guide.md` — where a guide belongs and how it
  is structured
- `dna/doc/guides/doc-guide.md` — the writing style: imperative headings,
  one step per line, commands in code blocks

## Skills

- `/guide` — reports duplicated content and style breaks in the existing
  guides, and writes new ones

## Layers

Orthogonal: this layer carries only its own topic and is combined with
other layers by the consuming repo.

## Variables

- `dnaCopyrightHolder` — the name in the license header of every file

## Usage

Declare it as a dev-dependency and initialize once:

```bash
pnpm add -D @ggdna/dna-guides   # TypeScript projects
dart pub add dev:dna_guides         # Dart projects
helix init
```

The placed test instantiates and verifies the DNA on every test run.

## Development

The `dna/` folder is hand-authored source and is never generated. The repo
instantiates its own DNA — run `dart test` after changes; commit first, a
file the DNA would overwrite must not carry uncommitted work.
