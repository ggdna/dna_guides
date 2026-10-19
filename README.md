# dna_guides

English | [Deutsch](README.de.md)

Gives a repo the rules for writing short, consistent guides and
documentation, and a skill that checks them.

## Motivation

Guides are read by people and by agents that follow them step by step.
The layer gives every repo the same few rules for them: short and
token-saving, written like a cookbook that addresses the reader directly,
one step per line, references to other guides instead of copies of their
content. The skill finds where the existing guides break these rules.

## Usage

Declare it as a dev-dependency and initialize once:

```bash
pnpm add -D @ggdna/dna-guides   # TypeScript projects
dart pub add dev:dna_guides     # Dart projects
helix init
```

`helix init` places a test that instantiates and verifies the DNA on every
test run. It copies the guides to `doc/guides/` and the skill to
`.claude/skills/guide/`.

Type `/guide` in Claude Code to have the existing guides reviewed or a new
one written. The skill reports duplicated content, headings that do not
read as a summary and steps that span more than one line, and lists every
file it wrote for review.

## Guides

- `dna/doc/guides/dna-guides-guide.md` — where a new English or German
  guide goes and how it is written: short, token-saving, cookbook style,
  referencing instead of duplicating
- `dna/doc/guides/doc-guide.md` — the writing style: imperative headings
  that read as a summary, one step per line, commands, code and screen
  elements as code, shell commands in bash code blocks

## Skills

- `/guide` — reports duplicated content and style breaks in the existing
  guides, and writes new ones; follows both guides

## Scope

The layer sets how guides are written, not what they say: the guides
themselves come from the repo and from the other layers. Translating
them is left to a translation layer such as dna_translate.

## Layers

The layer is orthogonal: `dna/_dna.json` lists no parent layers. It
carries only its own topic and is combined with other layers by the
consuming repo or by the umbrella layer of its organization.

## Variables

- `dnaCopyrightHolder` — the name in the license header of every file;
  `mustOverride` in `dna/_dna.json` marks it, so every repo that lists
  this layer sets it in its own `dna/_vars.json`

## Development

The `dna/` folder is hand-authored source and is never generated. The repo
instantiates its own DNA — run `dart test` after changes; commit first, a
file the DNA would overwrite must not carry uncommitted work.

Edit the files below `dna/`, not their copies in `doc/` and `.claude/`,
which the test overwrites.

## License

MIT — see [LICENSE](LICENSE).
