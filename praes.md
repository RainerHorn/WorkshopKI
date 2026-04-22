# Folienübersicht: Workshop „Lokale LLMs in der Praxis"

Datei: `html/praesentation.html`  
Grundlage: `README.md` + `NLQ_26.18.10_Arbeitsplan_KI BBS_final_v1.pdf`

---

| Nr. | Folientyp | Titel | Inhalt |
|-----|-----------|-------|--------|
| 1 | Titelfolie | Workshop: Lokale LLMs in der Praxis | Titel, Untertitel, Datum/Veranstaltung (NLQ 26.18.10, 27.04.2026), Referent |
| 2 | Inhaltsfolie | Lernziele | 5 Lernziele aus README (Unterschied Cloud/Lokal, Setups, Prompts, Praxisaufgaben, Chancen/Grenzen) |
| 3 | Inhaltsfolie | Zielgruppe & Voraussetzungen | Zweispaltig: Zielgruppe links, Hardware-/Software-Voraussetzungen rechts |
| 4 | Inhaltsfolie | Ablauf & Zeitplan | Tabelle der 5 Blöcke (Einstieg, Präsentation, Demo, Arbeit, Review) mit Zeitangaben |
| 5 | Inhaltsfolie | Was ist ein LLM? | Grundprinzipien verständlich erklärt: Transformer, Training, Inferenz, Token |
| 6 | Inhaltsfolie | Lokal vs. Cloud | Vergleichstabelle: Datenschutz, Kosten, Performance, Offline-Fähigkeit, Modellauswahl |
| 7 | Inhaltsfolie | Wichtige Begriffe | Glossar-Kacheln: Modell, Inferenz, Token, Kontextfenster, Quantisierung |
| 8 | Inhaltsfolie | Tools & Plattformen | Ollama, LM Studio, Open WebUI – jeweils kurze Beschreibung mit Einsatzempfehlung |
| 9 | Inhaltsfolie | Hardware & Performance | CPU/GPU, RAM/VRAM, Modellgrößen (3b / 7b / 70b) und empfohlene Mindestanforderungen |
| 10 | Inhaltsfolie | Sicherheit & Datenschutz | Lokale Datenhaltung, kein Cloud-Transfer, DSGVO-Aspekte, Offline-Betrieb |
| 11 | Inhaltsfolie | Grenzen lokaler Modelle | Realistische Erwartungen: Qualitätsunterschiede, Ressourcenbedarf, Aktualität der Modelle |
| 12 | Inhaltsfolie | Live-Demo: Ablauf | Start eines Modells, einfaches Prompting, schlechter vs. guter Prompt, Tipps für Reproduzierbarkeit |
| 13 | Aufgabenfolie | Beispiel A – Textzusammenfassung | Aufgabe + erwartetes Ergebnis; Hinweis: Prompt-Formulierung steuert Output |
| 14 | Aufgabenfolie | Beispiel B – Q&A auf eigene Inhalte | Aufgabe + erwartetes Ergebnis; Diskussion: Wo stoßen Modelle an Grenzen? |
| 15 | Aufgabenfolie | Beispiel C – Code & Automatisierung | Aufgabe + erwartetes Ergebnis; Regex / Shell-Skript / SQL erstellen oder Code erklären |
| 16 | Inhaltsfolie | Review & Abschluss | Best Practices, Nächste Schritte, Prompt-Cheatsheet-Hinweis |

---

## Hinweise zur Umsetzung

- **Titelfolie (1):** `.slide-title`-Layout (zentriert, ohne Panel, weiße Schrift auf Gradient)
- **Vergleich Lokal vs. Cloud (6):** `.comparison-table` innerhalb `.slide-panel`
- **Begriffe (7):** `.phases` + `.phase`-Kacheln
- **Aufgabenfolien (13–15):** `.task`-Box für Aufgabe, `.question`-Box für erwartetes Ergebnis
- **Hardware (9):** `.tech-specs`-Box
- **Grenzen (11):** `.warning`-Box für realistische Einschränkungen
- **Zweispaltige Folien (3, 12):** `.two-col`-Layout

## Navigation

Tastatur: `→` / `↓` / `Leertaste` = nächste Folie · `←` / `↑` = zurück  
Buttons: ◀ / ▶ (fest unten rechts)
