# Prompt Engineer Template - Wiederverwendbar

## 🎯 Standard-Template für prompt-engineer Aufrufe

Kopiere diesen Template und ersetze `[DEINE ANFORDERUNG HIER]` mit deiner aktuellen Anforderung:

```
Use prompt-engineer to help me create a technical prompt for the following requirement:

[DEINE ANFORDERUNG HIER]

CRITICAL INSTRUCTIONS for this session:
1. After the prompt-engineer generates the output, you (Claude) must STOP completely. Do NOT execute any code or invoke any agents.
2. The prompt-engineer should think carefully about the optimal agent chain and include a detailed recommendation with reasoning for each agent in the sequence.
3. The output should be clearly marked as "NOT EXECUTED - DRAFT ONLY"
4. I will manually review the generated prompt before deciding if/when to execute it.
5. Copy the prompt to a directory "./prompts/..." an name it fitting

Please ensure the prompt-engineer:
- Analyzes PROJECT_SCOPE.md for context, otherwise read and understand codebase
- Analyzes AGENT_LOG.md to understand the agent history
- Provides specific agent recommendations with clear reasoning
- Includes alternative agent chains if applicable
- Estimates complexity and duration
- Formats the output for easy copying
```

## 📋 Verwendungsbeispiele

### Beispiel 1: Performance Problem
```
Use prompt-engineer to help me create a technical prompt for the following requirement:

Die App ist morgens zwischen 7 und 9 Uhr extrem langsam, besonders beim Login.

CRITICAL INSTRUCTIONS for this session:
1. After the prompt-engineer generates the output, you (Claude) must STOP completely. Do NOT execute any code or invoke any agents.
2. The prompt-engineer should think carefully about the optimal agent chain and include a detailed recommendation with reasoning for each agent in the sequence.
3. The output should be clearly marked as "NOT EXECUTED - DRAFT ONLY"
4. I will manually review the generated prompt before deciding if/when to execute it.

Please ensure the prompt-engineer:
- Analyzes PROJECT_SCOPE.md for context
- Provides specific agent recommendations with clear reasoning
- Includes alternative agent chains if applicable
- Estimates complexity and duration
- Formats the output for easy copying
```

### Beispiel 2: Feature Request
```
Use prompt-engineer to help me create a technical prompt for the following requirement:

Ich möchte dass User ihre Dashboard-Widgets per Drag&Drop anordnen können, wie bei Notion.

CRITICAL INSTRUCTIONS for this session:
1. After the prompt-engineer generates the output, you (Claude) must STOP completely. Do NOT execute any code or invoke any agents.
2. The prompt-engineer should think carefully about the optimal agent chain and include a detailed recommendation with reasoning for each agent in the sequence.
3. The output should be clearly marked as "NOT EXECUTED - DRAFT ONLY"
4. I will manually review the generated prompt before deciding if/when to execute it.

Please ensure the prompt-engineer:
- Analyzes PROJECT_SCOPE.md for context
- Provides specific agent recommendations with clear reasoning
- Includes alternative agent chains if applicable
- Estimates complexity and duration
- Formats the output for easy copying
```

### Beispiel 3: Bug Report
```
Use prompt-engineer to help me create a technical prompt for the following requirement:

Kunde meldet: "ERROR 500 bei Bestellungen über 1000€, aber nur Freitags"

CRITICAL INSTRUCTIONS for this session:
1. After the prompt-engineer generates the output, you (Claude) must STOP completely. Do NOT execute any code or invoke any agents.
2. The prompt-engineer should think carefully about the optimal agent chain and include a detailed recommendation with reasoning for each agent in the sequence.
3. The output should be clearly marked as "NOT EXECUTED - DRAFT ONLY"
4. I will manually review the generated prompt before deciding if/when to execute it.

Please ensure the prompt-engineer:
- Analyzes PROJECT_SCOPE.md for context
- Provides specific agent recommendations with clear reasoning
- Includes alternative agent chains if applicable
- Estimates complexity and duration
- Formats the output for easy copying
```

## 🚀 Kurz-Version für Profis

Wenn du die Kontrolle bereits verinnerlicht hast, reicht auch:

```
prompt-engineer (NO EXECUTION): [DEINE ANFORDERUNG]
Remember: Output only, detailed agent chain reasoning required.
```

## 💡 Pro-Tipps

1. **Speichere diesen Template** in deinem Projekt unter `.claude/templates/prompt-engineer.md`

2. **Erstelle Shortcuts** in deinem Editor:
   ```bash
   # VS Code Snippet
   "Prompt Engineer": {
     "prefix": "pe",
     "body": [
       "Use prompt-engineer to help me create a technical prompt for the following requirement:",
       "",
       "$1",
       "",
       "CRITICAL INSTRUCTIONS for this session:",
       "1. After the prompt-engineer generates the output, you (Claude) must STOP completely. Do NOT execute any code or invoke any agents.",
       "2. The prompt-engineer should think carefully about the optimal agent chain and include a detailed recommendation with reasoning for each agent in the sequence.",
       "3. The output should be clearly marked as 'NOT EXECUTED - DRAFT ONLY'",
       "4. I will manually review the generated prompt before deciding if/when to execute it."
     ]
   }
   ```

3. **Erweitere bei Bedarf**:
   - Füge spezifische Kontexte hinzu
   - Ergänze Präferenzen für Agent-Auswahl
   - Definiere Output-Format-Wünsche

## 🎨 Anpassbare Varianten

### Für Doku-Fokus:
```
[Standard Template]
+ Additionally, ensure all documentation agents (doc-writer, codebase-analyst) are considered in the chain.
```

### Für Security-Fokus:
```
[Standard Template]
+ Pay special attention to security implications and include security-scanner in the agent chain if relevant.
```

### Für Performance-Fokus:
```
[Standard Template]
+ Emphasize performance profiling agents and include specific metrics in the requirements.
```

---

Speichere diesen Template und nutze ihn als Ausgangspunkt für alle deine prompt-engineer Anfragen!
