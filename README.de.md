# dna_guides

[English](README.md) | Deutsch

Gibt einem Repo die Regeln für kurze, einheitliche Guides und
Dokumentation und einen Skill, der sie prüft.

## Motivation

Guides lesen Menschen und Agenten, die ihnen Schritt für Schritt folgen.
Die Schicht gibt jedem Repo dieselben wenigen Regeln dafür: kurz und
tokensparend, wie ein Kochbuch geschrieben, das den Leser direkt
anspricht, ein Schritt pro Zeile, Verweise auf andere Guides statt Kopien
ihres Inhalts. Der Skill findet, wo die vorhandenen Guides diese Regeln
brechen.

## Verwendung

Als Dev-Dependency eintragen und einmal initialisieren:

```bash
pnpm add -D @ggdna/dna-guides   # TypeScript projects
dart pub add dev:dna_guides     # Dart projects
helix init
```

`helix init` legt einen Test ab, der die DNA bei jedem Testlauf
instanziiert und prüft. Er legt die Guides in `doc/guides/` ab und den
Skill in `.claude/skills/guide/`.

Tippe `/guide` in Claude Code, um die vorhandenen Guides prüfen oder einen
neuen schreiben zu lassen. Der Skill meldet doppelte Inhalte, Überschriften,
die zusammen keine Zusammenfassung ergeben, und Schritte über mehr als
eine Zeile, und listet jede Datei, die er geschrieben hat, zur Durchsicht
auf.

## Guides

- `dna/doc/guides/dna-guides-guide.md` — wohin ein neuer englischer oder
  deutscher Guide kommt und wie er geschrieben wird: kurz, tokensparend,
  im Kochbuchstil, verweisen statt doppeln
- `dna/doc/guides/doc-guide.md` — der Schreibstil: Überschriften im
  Imperativ, die zusammen eine Zusammenfassung ergeben, ein Schritt pro
  Zeile, Befehle, Code und Bildschirmelemente als Code, Shell-Befehle in
  bash-Codeblöcken

## Skills

- `/guide` — meldet doppelte Inhalte und Stilbrüche in den vorhandenen
  Guides und schreibt neue; folgt beiden Guides

## Umfang

Die Schicht legt fest, wie Guides geschrieben werden, nicht, was in ihnen
steht: Die Guides selbst kommen aus dem Repo und aus den anderen
Schichten. Das Übersetzen überlässt sie einer Übersetzungs-Schicht wie
dna_translate.

## Schichten

Die Schicht ist orthogonal: `dna/_dna.json` nennt keine Eltern-Schichten.
Sie trägt nur ihr eigenes Thema und wird vom nutzenden Repo oder von der
Umbrella-Schicht seiner Organisation mit anderen Schichten kombiniert.

## Variablen

- `dnaCopyrightHolder` — der Name im Lizenzkopf jeder Datei;
  `mustOverride` in `dna/_dna.json` markiert ihn, daher setzt ihn jedes
  Repo, das diese Schicht einbindet, in seiner eigenen `dna/_vars.json`

## Entwicklung

Der Ordner `dna/` ist handgeschriebene Quelle und wird nie generiert. Das
Repo instanziiert seine eigene DNA — nach Änderungen `dart test` laufen
lassen; vorher committen, denn eine Datei, die die DNA überschreiben
würde, darf keine uncommittete Arbeit enthalten.

Bearbeite die Dateien unter `dna/`, nicht ihre Kopien in `doc/` und
`.claude/`, die der Test überschreibt.

## Lizenz

MIT — siehe [LICENSE](LICENSE).
