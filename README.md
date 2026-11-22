# 4EA Public Resources

Öffentliche Anleitungen von **4EA.tech** – praxisnah, werkzeugunabhängig und zum Weiterverwenden. Die Sammlung wird
unter anderem von [ai.4ea.tech](https://ai.4ea.tech) genutzt.

## Was hier liegt

- **Anleitungen** für wiederkehrende Aufgaben mit AI-Werkzeugen und in der Architekturarbeit
- **Titelbilder** und Illustrationen zu den Anleitungen
- **Code-Beispiele** in den Anleitungen, wo sie das Verständnis fördern

## Aufbau

```
guides/
  <id>/
    index.md      # Anleitung mit Frontmatter
    cover.svg     # Titelbild
    bild.png      # weitere Bilder, relativ verlinkt
```

Jede Anleitung liegt in einem eigenen Ordner `guides/<id>/`. Die `id` ist kebab-case, die Anleitung selbst steht in
`index.md`. Bilder liegen im selben Ordner und werden relativ eingebunden.

Das vollständige Format – Frontmatter, Bildregeln, Titelbild und Checkliste vor dem Veröffentlichen – steht in
[FORMAT.md](FORMAT.md).

## Lizenz

- **Texte und Bilder:** [Creative Commons Namensnennung 4.0 International (CC BY 4.0)](LICENSE) – Namensnennung
  «4EA.tech».
- **Code-Beispiele:** [MIT](LICENSE-CODE) – Copyright «4EA.tech».

Du darfst die Inhalte teilen und bearbeiten, auch kommerziell, solange du die Quelle nennst und die Lizenzbedingungen
einhältst.
