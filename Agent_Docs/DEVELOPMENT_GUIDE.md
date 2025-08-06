# Agent Development Guide

## Übersicht

Dieses Verzeichnis enthält persönliche Claude Agent-Definitionen. Hier werden regelmäßig Anpassungen und Verbesserungen an den Agenten vorgenommen.

## Wichtige Konventionen für Agent-Anpassungen

### 1. Projektkontext-Integration
Alle Agenten sollten relevante Projektdokumentation lesen, bevor sie ihre Hauptaufgabe ausführen:
- `PROJECT_SCOPE.md` oder `project-scope.md`
- `CLAUDE.md` oder `claude.md` 
- `README.md`
- Weitere projektspezifische Dokumentation

### 2. Output-Verzeichnisse
Agenten, die Dateien generieren, sollten diese in strukturierten Verzeichnissen ablegen:
- `prompts/` - Für generierte Prompts (prompt-engineer)
- `docs/` - Für generierte Dokumentation (doc-writer)
- `tests/` - Für generierte Tests (test-engineer)
- `reports/` - Für Review-Berichte (code-reviewer)

### 3. Tool-Zugriff
Beim Anpassen von Agenten darauf achten, dass alle benötigten Tools in der Tool-Liste enthalten sind:
```yaml
tools: Glob, Grep, LS, Read, Write, Edit, MultiEdit, NotebookRead, NotebookEdit, WebFetch, TodoWrite, WebSearch
```

### 4. Agent-Koordination
- Alle Agenten nutzen `AGENT_LOG.md` für die Kommunikation untereinander
- Agenten sollten ihre Ergebnisse strukturiert in AGENT_LOG.md dokumentieren
- Nachfolgende Agenten lesen AGENT_LOG.md, um auf vorherigen Ergebnissen aufzubauen

### 5. Namenskonventionen für generierte Dateien
- Feature: `feature-[kurzbeschreibung]-[datum].md`
- Bugfix: `bugfix-[komponente]-[datum].md`
- Performance: `perf-[bereich]-[datum].md`
- Research: `research-[thema]-[datum].md`

## Typische Anpassungen

### Beispiel: Agent mit Datei-Output erweitern
```markdown
**Working Process**:
1. FIRST: Read project documentation to understand context
2. [Weitere Schritte...]
13. SAVE output to [directory]/[descriptive-name].md
14. STOP COMPLETELY - do not continue processing

**Automatic File Saving**:
ALWAYS save the generated output to [directory]/[descriptive-name].md
```

### Beispiel: Projektkontext-Integration hinzufügen
```markdown
**📂 FIRST STEPS - PROJECT UNDERSTANDING**
Before starting main task, you MUST:
1. Check for project documentation in this order:
   - PROJECT_SCOPE.md or project-scope.md
   - CLAUDE.md or claude.md
   - README.md
```

## Best Practices

1. **Klare Verantwortungsbereiche**: Jeder Agent sollte einen klar definierten Aufgabenbereich haben
2. **Explizite Stopps**: Agenten sollten nach ihrer Hauptaufgabe stoppen und nicht eigenständig weitermachen
3. **Dokumentation lesen**: Immer zuerst verfügbare Projektdokumentation verstehen
4. **Strukturierte Ausgabe**: Outputs in sinnvollen Verzeichnissen organisieren
5. **Tool-Verfügbarkeit**: Sicherstellen, dass alle benötigten Tools (insbesondere Write) verfügbar sind

## Wartungshinweise

- Bei Änderungen immer die Tool-Liste überprüfen
- Beispiele in der Agent-Description aktualisieren
- Working Process Schritte durchnummerieren für Klarheit
- AGENT_LOG.md Nutzung konsistent halten

## Kontakt

Bei Fragen oder Verbesserungsvorschlägen gerne ein Issue im Repository erstellen.