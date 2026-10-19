# ha-utils – Agent-Regeln

## Blueprint-Versionen (PFLICHT)

Bei jeder Erstellung oder Änderung eines Home-Assistant-Blueprints
(`*.yaml` mit `blueprint:` und `description:`) ist zwingend der Skill
`blueprint-version` zu laden und die `Version:`-Zeile in der `description`
zu aktualisieren — ohne Ausnahme, auch bei kleinsten Änderungen und
Bugfixes, auch ohne ausdrückliche Aufforderung. Kein Commit eines
geänderten Blueprints ohne aktualisierte `Version:`-Zeile. Vor dem Commit
per `grep` prüfen, dass genau eine `Version:`-Zeile vorhanden ist.