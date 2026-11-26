# Example

`dna_guides` is a DNA layer: it ships the rules for writing guides and
documentation and the `/guide` skill, no library code. Declare it as a dev
dependency and instantiate it once:

```bash
dart pub add dev:dna_guides    # Dart projects
pnpm add -D @ggdna/dna-guides  # TypeScript projects
gg dna init
gg dna build
```

Then type `/guide` in Claude Code to write or check a guide in
`doc/en/guides`, translated in `doc/de/guides` and `doc/fa/guides`.
