---
name: blueprint-version
description: >
  MANDATORY: Versionsnummer in der description von Home-Assistant-Blueprints pflegen (Format Version: yyyy-mm-dd[.Zähler]).
  NIEMALS ÜBERGEHEN. Lade diesen Skill IMMER und bedingungslos, sobald ein Blueprint (*.yaml mit blueprint: und description:)
  erstellt oder geändert wird — auch bei kleinsten Änderungen und Bugfixes — oder wenn der Nutzer
  "Version", "Blueprint-Version" oder "versionieren" erwähnt. Jede Blueprint-Änderung erfordert einen Versions-Bump.
---

# Blueprint-Version

**PFLICHT / MANDATORY — NIEMALS ÜBERGEHEN.** Jede Erstellung oder Änderung eines
Home-Assistant-Blueprints (`*.yaml` mit `blueprint:` und `description:`) erfordert
zwingend eine Versionsaktualisierung in der `description` — ohne Ausnahme, auch bei
kleinsten Änderungen, auch bei reinen Bugfixes, auch wenn der Nutzer es nicht explizit
verlangt. Kein Commit eines geänderten Blueprints ohne aktualisierte `Version:`-Zeile.
Bei Verstoß: Arbeit als unvollständig betrachten und nachholen.

Jede Erstellung oder Änderung eines Home-Assistant-Blueprints bekommt eine Versionsnummer
in der `description` des Blueprints.

## Format

- Eigene Zeile innerhalb von `blueprint.description`, vorangestellt `Version: `.
- Schema: `Version: yyyy-mm-dd` für die erste Version des Tages,
  danach `Version: yyyy-mm-dd.N` mit hochzählendem `N` (1, 2, 3, …).
- Datum ist das aktuelle Kalenderdatum (Format `yyyy-mm-dd`, z. B. `2026-10-13`).
- Bestehende Schreibweisen wie `Version 2026-10-13` werden auf `Version: …` normalisiert.

Beispiel innerhalb der Description:

```yaml
blueprint:
  description: >
    Was der Blueprint tut.

    Version: 2026-10-13.1

    Hinweis: …
```

## Vorgehen

1. Geänderte Blueprint-Datei öffnen und die vorhandene Versionszeile suchen
   (Regex: `^\\s*Version:?\\s*(\\d{4}-\\d{2}-\\d{2})(?:\\.(\\d+))?`).
2. Neue Version bestimmen:
   - Keine Versionszeile vorhanden → `Version: <heute>` einfügen.
   - Datum der vorhandenen Version ist älter als heute → auf `Version: <heute>` setzen (Zähler zurücksetzen).
   - Datum ist heute ohne Zähler (z. B. `Version: 2026-10-13`) → `Version: <heute>.1`.
   - Datum ist heute mit Zähler `N` → `Version: <heute>.N+1`.
3. Genau eine Versionszeile als eigenen Absatz in der Description pflegen
   (hinter den Funktions-Bullets, vor Hinweisen wie z. B. Himmelsrichtung).
   Keine zweite Versionszeile stehen lassen.
4. Vor einem Commit per `grep` prüfen, dass jede geänderte Blueprint-Datei
   genau eine Zeile `Version: …` enthält.
