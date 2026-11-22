# Format für Anleitungen

Diese Datei beschreibt, wie eine Anleitung in diesem Repo aufgebaut ist. Sie gilt für alle Beiträge und für den
Import in ai.4ea.tech.

## Ordnerstruktur

```
guides/
  <id>/
    index.md
    cover.svg
    bild.png
    ...
```

- `<id>` ist **kebab-case**: nur Kleinbuchstaben, Ziffern und Bindestriche (`[a-z0-9-]+`), keine Umlaute, keine
  Leerzeichen. Beispiel: `token-sparen-claude-code`.
- Pro Anleitung genau ein Ordner. `index.md` und `cover.svg` sind Pflicht.
- Weitere Bilder liegen im **gleichen Ordner** wie `index.md`.

## `index.md`: Frontmatter

Die Datei beginnt mit einem YAML-Block zwischen `---`-Zeilen. Erlaubt sind **nur** einfache Zeilen der Form:

```yaml
key: wert
key: "wert"
key: [a, b]
```

Nicht erlaubt: verschachtelte Objekte, Blocklisten mit `-`, mehrzeilige Texte, Anführungszeichen über mehrere Zeilen.

### Pflichtfelder

| Key | Typ | Regel |
|---|---|---|
| `title` | Text | Titel der Anleitung, höchstens 120 Zeichen |
| `summary` | Text | Kurzfassung für Listen und Suche, höchstens 600 Zeichen |
| `ea_note` | Text | Einordnung für Enterprise-Architekten, höchstens 400 Zeichen |
| `level` | Text | `einstieg`, `vertiefung` oder `experte` |
| `language` | Text | Sprachcode nach ISO 639-1, z. B. `de` oder `en` |
| `concepts` | Liste | Bezug zu Begriffen, z. B. `[prompt, kontextfenster]`; darf leer sein: `[]` |
| `apps` | Liste | Ziel-Apps, z. B. `[ai]` |

Beispiel:

```yaml
---
title: "Token sparen mit Claude Code"
summary: "Wie du den festen Kontextblock misst und mit wenigen Eingriffen kleiner hältst."
ea_note: "Hilft, Agentenkosten und Tempo einzuordnen, ohne die Sicherheitsregeln zu verwässern."
level: vertiefung
language: de
concepts: []
apps: [ai]
---
```

Der Frontmatter-Block wird beim Import validiert. Fehlt ein Pflichtfeld oder stimmt ein Wert nicht, wird die Anleitung
nicht übernommen.

## Inhalt

- Markdown **ohne** `#`-Überschrift: Der Titel kommt aus `title`. Abschnitte beginnen mit `##`.
- Deutsch in der Schweiz: «ss» statt «ß», «du»-Form, sachlich.
- Konkrete Schritte statt allgemeiner Ratschläge; wo sinnvoll mit Prompt-Beispielen und Checkliste.
- Keine internen Pfade, Firmennamen, Personennamen, Zugangsdaten oder Messwerte aus einem bestimmten Projekt.
  Grössenordnungen als Richtwerte formulieren («oft mehrere tausend Tokens»).

## Bilder

- Formate: **png**, **jpg** oder **webp**.
- Im gleichen Ordner wie `index.md` ablegen, relativ und ohne führenden Slash verlinken:

  ```markdown
  ![Aufbau der Pipeline](pipeline.png)
  ```

- Externe Bild-URLs sind nicht erlaubt. So bleibt die Anleitung unabhängig und der Import kontrollierbar.
- Vor dem Veröffentlichen die Metadaten entfernen (EXIF, GPS, Kameramodell, Softwarehinweise). Bilder ohne
  Personenbezug wählen.

## `cover.svg`: Titelbild

Das Titelbild ist eine flache Illustration im Stil der 4EA.tech-Website.

- `viewBox="0 0 640 320"`, keine festen `width`/`height`-Attribute.
- Flächig, ohne Texte, Schatten oder Verläufe. Höchstens **ein** Element oder eine Gruppe mit `class="accent"`.
- Formen tragen eine der Klassen `dark`, `mid`, `light` oder `accent`. Ein `<style>`-Block setzt Ersatzfarben für
  helle und dunkle Darstellung.
- Verboten: `script`, `foreignObject`, `image`, `a`, `href`, Event-Attribute und externe Referenzen.
- Das Motiv muss auch bei 320 px Breite klar lesbar sein.

## Checkliste vor dem Veröffentlichen

- [ ] Ordner-ID ist kebab-case und eindeutig
- [ ] `index.md` und `cover.svg` vorhanden
- [ ] Frontmatter vollständig, nur einfache `key: wert`-Zeilen, Längen eingehalten
- [ ] `summary` und `ea_note` innerhalb der Grenzen
- [ ] Keine Interna: keine privaten Repo-Pfade, Firmen- oder Personennamen, Domains ausser `4ea.tech` und
      `ai.4ea.tech`, keine Agenten- oder Infrastruktur-Interna
- [ ] Keine Secrets, Tokens, Zugangsdaten oder internen URLs
- [ ] Bilder im gleichen Ordner, relativ verlinkt, ohne Metadaten
- [ ] `cover.svg` regelkonform und ohne externe Referenzen
- [ ] Rechtschreibung geprüft (Schweizer Schreibweise)
- [ ] Lizenzhinweis passt: Texte und Bilder CC BY 4.0, Code-Beispiele MIT
