# Agent Chain Examples - Bewährte Workflows

Dieses Dokument zeigt bewährte Agent-Ketten für häufige Entwicklungsaufgaben. Jede Kette nutzt die Stärken der einzelnen Agenten optimal aus.

## 🔍 Debugging-Workflow

### Einfaches Bug-Fixing
```
1. prompt-engineer
   → Problem klar definieren und technische Requirements extrahieren
   → Output: prompts/bugfix-[component]-[date].md

2. code-reviewer
   → Betroffenen Code analysieren, Root Cause identifizieren
   → Output: AGENT_LOG.md mit Findings

3. python-generator
   → Fix basierend auf code-reviewer Findings implementieren
   → Liest: AGENT_LOG.md für Context

4. test-engineer
   → Tests schreiben, die den Bug reproduzieren und Fix verifizieren
   → Output: tests/ mit neuen Testfällen

5. claude-status
   → Metriken aktualisieren, Bug-Fix dokumentieren
   → Updates: Claude.md Dashboard
```

### Komplexes Performance-Debugging
```
1. prompt-engineer
   → Performance-Problem in messbare Metriken übersetzen
   → "Die App ist langsam" → "API Response >500ms bei 100 concurrent users"

2. architect-cleaner
   → Architecture Review mit Fokus auf Performance-Bottlenecks
   → Identifiziert: Strukturelle Probleme, Tech Debt

3. code-reviewer
   → Detaillierte Code-Analyse der kritischen Pfade
   → Output: Performance-Hotspots in AGENT_LOG.md

4. python-generator
   → Optimierungen implementieren (Caching, Async, Batching)
   → Basiert auf: architect-cleaner + code-reviewer Findings

5. test-engineer
   → Performance-Tests und Benchmarks erstellen
   → Verifiziert: Improvements messbar

6. doc-writer
   → Performance-Optimierungen dokumentieren
   → Updates: Architecture docs, API docs

7. claude-status
   → Performance-Metriken tracken
   → Zeigt: Vorher/Nachher Vergleich
```

## 🧹 Repository-Aufräumen

### Wöchentliche Wartung
```
1. architect-cleaner
   → Umfassende Analyse und aggressives Cleanup
   → Erstellt: PROJECT_SCOPE.md, ERROR_LOG.md (falls fehlend)
   → Löscht: Obsolete Files, Cache, Dead Code
   → Output: CLEANUP_REPORT.md mit allen Aktionen

2. doc-writer
   → Dokumentation an neue Struktur anpassen
   → Aktualisiert: README.md, API docs
   → Entfernt: Docs für gelöschten Code

3. claude-status
   → Cleanup-Metriken erfassen
   → Reports: Space saved, Files deleted, Health Score
```

### Major Refactoring
```
1. prompt-engineer
   → Refactoring-Ziele klar definieren
   → Erstellt: Structured plan mit Metriken

2. architect-cleaner
   → Baseline etablieren, Current State dokumentieren
   → Identifiziert: Refactoring-Kandidaten

3. python-generator
   → Neue Struktur implementieren
   → Folgt: Clean Architecture Patterns

4. test-engineer
   → Umfassende Test-Coverage sicherstellen
   → Migration Tests für Refactoring

5. code-reviewer
   → Neue Struktur reviewen
   → Prüft: Pattern-Consistency, Best Practices

6. architect-cleaner
   → Post-Refactoring Cleanup
   → Entfernt: Alte Struktur, Migration Code

7. doc-writer
   → Neue Architecture dokumentieren
   → Updates: Alle relevanten Docs

8. claude-status
   → Refactoring-Impact messen
   → Zeigt: Complexity reduction, Coverage increase
```

## 🚀 Neues Feature entwickeln

### Standard Feature-Entwicklung
```
1. prompt-engineer
   → User Story in technische Requirements übersetzen
   → Definiert: Success Criteria, Constraints
   → Output: prompts/feature-[name]-[date].md

2. python-generator
   → Feature implementieren
   → Nutzt: Context7 für aktuelle Library-Docs
   → Folgt: PROJECT_SCOPE.md Patterns

3. test-engineer
   → Comprehensive Test Suite
   → Unit Tests, Integration Tests, Edge Cases

4. code-reviewer
   → Security und Quality Review
   → Prüft: Vulnerabilities, Performance, Standards

5. doc-writer
   → Feature-Dokumentation
   → API Docs, Usage Examples, Migration Guide

6. claude-status
   → Feature-Completion tracken
   → Updates: Development velocity, Coverage
```

### Complex Feature mit UI/Backend
```
1. prompt-engineer
   → Zerlegt Feature in Frontend/Backend Tasks
   → Definiert: API Contract, UI Requirements

2. architect-cleaner
   → Prüft Architecture-Fit
   → Schlägt vor: Optimal integration points

3. python-generator (Backend)
   → API Endpoints implementieren
   → Database Models, Business Logic

4. python-generator (Frontend Integration)
   → Frontend-Backend Integration
   → API Clients, State Management

5. test-engineer
   → E2E Tests, API Tests, Unit Tests
   → Testet: Complete User Journey

6. code-reviewer
   → Full-Stack Review
   → Security, Performance, UX

7. doc-writer
   → Vollständige Feature-Docs
   → User Guide, API Reference, Architecture

8. claude-status
   → Feature-Metriken
   → Complexity, Test Coverage, Performance
```

## 🔄 Continuous Improvement Workflow

### Daily Development Flow
```
Morning:
1. claude-status → Check yesterday's metrics
2. architect-cleaner → Quick health check

During Development:
3. prompt-engineer → Clarify any vague requirements
4. python-generator → Implement features
5. test-engineer → Write tests alongside code

End of Day:
6. code-reviewer → Review day's work
7. doc-writer → Update changed docs
8. claude-status → Generate daily summary
```

### Weekly Maintenance
```
Monday:
1. architect-cleaner → Full repository scan
2. doc-writer → Update outdated docs

Wednesday:
3. code-reviewer → Review week's changes
4. test-engineer → Improve test coverage

Friday:
5. claude-status → Weekly report
6. prompt-engineer → Plan next week's tasks
```

## 💡 Best Practices

### Agent-Kommunikation
- **AGENT_LOG.md** ist das zentrale Kommunikationsmedium
- Jeder Agent liest vorherige Einträge
- Jeder Agent schreibt strukturierte Findings
- Nachfolgende Agents bauen auf vorherigen auf

### Fehlerbehandlung
```
Wenn ein Agent fehlschlägt:
1. ERROR_LOG.md → Agent trägt Fehler ein
2. prompt-engineer → Erstellt präzisen Fix-Prompt
3. Entsprechender Agent → Führt Fix aus
4. claude-status → Trackt Resolution Time
```

### Parallelisierung
Manche Agents können parallel laufen:
```
Parallel möglich:
- code-reviewer + test-engineer (auf verschiedenen Modulen)
- doc-writer + claude-status (verschiedene Outputs)

Sequenziell erforderlich:
- prompt-engineer → andere Agents (brauchen klare Requirements)
- python-generator → test-engineer (Tests brauchen Code)
- architect-cleaner → doc-writer (Docs brauchen finale Struktur)
```

### Projektgröße beachten

#### Kleine Projekte (<10k LOC)
- Fokus auf: python-generator, test-engineer, doc-writer
- architect-cleaner: Monatlich
- Einfachere Agent-Ketten

#### Mittlere Projekte (10k-100k LOC)
- Alle Agents regelmäßig nutzen
- architect-cleaner: Wöchentlich
- Strukturierte AGENT_LOG.md wichtig

#### Große Projekte (>100k LOC)
- architect-cleaner: 2x wöchentlich
- Mehrere parallele Agent-Ketten
- Detaillierte ERROR_LOG.md pflege
- Automatisierung der Ketten empfohlen

## 📊 Metriken für Erfolg

### Key Performance Indicators
1. **Code Quality**
   - Coverage: >80% (via test-engineer)
   - Complexity: <10 (via architect-cleaner)
   - Security Issues: 0 (via code-reviewer)

2. **Documentation**
   - Coverage: >90% (via doc-writer)
   - Aktualität: <7 Tage (via doc-writer)

3. **Repository Health**
   - Health Score: >9/10 (via architect-cleaner)
   - Build Time: <5min (via architect-cleaner)
   - Tech Debt: <5 days (via architect-cleaner)

4. **Development Velocity**
   - Features/Week: Tracked (via claude-status)
   - Bug Resolution: <24h (via claude-status)
   - Test Writing: Parallel to code (via test-engineer)

## 🚨 Wann welchen Agent?

### Sofort-Trigger
- **architect-cleaner**: Build wird langsam, Repo feels cluttered
- **code-reviewer**: Nach jedem größeren Commit
- **test-engineer**: Bei Coverage <80%
- **doc-writer**: Bei neuen Public APIs
- **prompt-engineer**: Bei unklaren Requirements

### Regelmäßige Trigger
- **Daily**: claude-status (End-of-day summary)
- **Weekly**: architect-cleaner (Monday morning)
- **Per Feature**: Vollständige Feature-Kette
- **Per Bug**: Debug-Kette

### Proaktive Nutzung
Die Agents sollten proaktiv genutzt werden:
- Nicht warten bis Problems auftreten
- Regelmäßige Health Checks
- Kontinuierliche Verbesserung
- Frühe Dokumentation

## 🎯 Beispiel: Real-World Szenario

**Aufgabe**: "Die Payment-Integration funktioniert nicht mehr richtig"

```
1. prompt-engineer
   Input: "Die Payment-Integration funktioniert nicht mehr richtig"
   Output: Spezifische Fehler-Requirements in prompts/bugfix-payment-2024-01-15.md
   - Affected: Stripe webhook processing
   - Error: 500 on amounts >$1000
   - Started: After v2.3.1 deployment

2. code-reviewer
   Analysiert: payment_service.py, webhook_handler.py
   Findet: Integer overflow in amount calculation
   Dokumentiert: Security implications in AGENT_LOG.md

3. python-generator
   Implementiert: Safe amount handling with Decimal
   Adds: Input validation, error handling
   Follows: OWASP secure coding practices

4. test-engineer
   Schreibt: Edge case tests for large amounts
   Adds: Webhook signature validation tests
   Coverage: 95% for payment module

5. code-reviewer (Second Pass)
   Verifiziert: Fix is secure and complete
   Confirms: No side effects

6. doc-writer
   Updates: API docs with amount limits
   Adds: Troubleshooting guide
   Documents: Webhook retry logic

7. claude-status
   Reports: Bug fixed in 3.5 hours
   Updates: Payment processing metrics
   Notes: Similar issues to watch
```

**Resultat**: Strukturierter Fix mit vollständiger Dokumentation und Tests.

---

Dieser Guide wird kontinuierlich erweitert basierend auf praktischen Erfahrungen mit den Agent-Ketten.