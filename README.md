# Workshop: Lokale LLMs in der Praxis (3-4 Stunden)

## Ziel des Workshops
Dieser Workshop gibt einen kompakten Überblick zur Nutzung lokaler Large Language Models (LLMs) und führt die Teilnehmenden anschließend durch 2-3 konkrete Praxisbeispiele, die sie selbst erarbeiten.

## Zielgruppe
- Entwicklerinnen und Entwickler
- Tech-affine Fachbereiche
- Teams, die mit KI arbeiten möchten, aber lokale Datenhaltung bevorzugen

## Lernziele
Am Ende des Workshops können die Teilnehmenden:
- den Unterschied zwischen Cloud-LLMs und lokalen LLMs erklären,
- typische lokale LLM-Setups benennen,
- Prompts strukturiert formulieren,
- 2-3 praktische Aufgaben mit einem lokalen Modell selbstständig umsetzen,
- Chancen und Grenzen lokaler LLMs einschätzen.

## Voraussetzungen der Teilnehmenden
- Grundlegendes Verständnis von Software und Texteditoren
- Laptop mit mindestens 16 GB RAM (32 GB empfohlen)
- Lokales LLM-Tool vorab installiert (Anleitung wird vorab versendet)
- Keine KI-Vorkenntnisse erforderlich

## Zeitrahmen und Ablauf (3-4 Stunden)

| Block | Inhalt | Zeit |
|-------|--------|------|
| 1 | Einstieg und Kontext | 15–20 min |
| 2 | Überblick als Präsentation | 45–60 min |
| 3 | Live-Demo | 20–30 min |
| 4 | Teilnehmerarbeit (2–3 Beispiele) | 90–120 min |
| 5 | Ergebnis-Review und Abschluss | 20–30 min |
| **Gesamt** | | **190–260 min** |

### 1) Einstieg und Kontext (15-20 min)
- Begrüßung und Zielbild
- Erwartungsabfrage
- Wann lokale LLMs sinnvoll sind (Datenschutz, Kostenkontrolle, Offline-Nutzung)

### 2) Überblick als Präsentation (45-60 min)
Inhalte der Präsentation:
- Was ist ein LLM? Grundprinzipien verständlich erklärt
- Lokale vs. Cloud-Nutzung: Vor- und Nachteile
- Wichtige Begriffe: Modell, Inferenz, Token, Kontextfenster, Quantisierung
- Typische Tools und Plattformen (z. B. Ollama, LM Studio, Open WebUI)
- Hardware- und Performance-Grundlagen (CPU/GPU, RAM/VRAM)
- Sicherheit und Datenschutz bei lokalem Einsatz
- Grenzen lokaler Modelle und realistische Erwartungen

### 3) Live-Demo (20-30 min)
- Start eines lokalen Modells
- Einfaches Prompting
- Kurzer Vergleich: schlechter Prompt vs. guter Prompt
- Tipps für reproduzierbare Ergebnisse

### 4) Teilnehmerarbeit: 2-3 konkrete Beispiele (90-120 min)
Die Teilnehmenden bearbeiten in kleinen Gruppen oder einzeln 2-3 Aufgaben.

#### Beispiel A: Textzusammenfassung und Strukturierung

**Aufgabe:**
- Einen längeren Text lokal zusammenfassen
- Ergebnis in Stichpunkten und als Executive Summary ausgeben

**Erwartetes Ergebnis:**
- Klar strukturierte, kurze Zusammenfassung
- Verständnis dafür, wie Prompt-Formulierungen das Ergebnis steuern

#### Beispiel B: Lernstandsanalyse und individuelles Feedback (BBS-Kontext)

**Aufgabe:**
- Anonymisierte oder pseudonymisierte Beurteilungsnotizen bzw. Kompetenzraster aus dem BBS-Alltag als Kontext einfügen
- Das lokale LLM individuelle Rückmeldungen, Förderpläne oder Zeugnisformulierungen daraus ableiten lassen
- Gezielt testen, wie das Modell reagiert, wenn personenbezogene Daten (Name, Geburtsdatum) im Kontext enthalten sind

**Erwartetes Ergebnis:**
- Differenzierte, textlich brauchbare Entwürfe für Schülerrückmeldungen
- Bewusstsein dafür, welche Daten lokal verarbeitet werden dürfen und welche nicht
- Diskussion: Pseudonymisierung als Voraussetzung für den LLM-Einsatz in Schule und Bildungsverwaltung

#### Beispiel C: Automatisierte Dokumentenerstellung mit personengebundenen Daten (BBS-Kontext)

**Aufgabe:**
- Vorlagen für typische BBS-Dokumente erstellen lassen, die personengebundene Daten enthalten oder referenzieren (z. B. Zeugnistexte, Elternbriefe, Gesprächsprotokolle, Praktikumsbeurteilungen)
- Mit dem lokalen Modell eine kleine Hilfsfunktion (z. B. Skript oder Prompt-Kette) erarbeiten, die echte Namen automatisch durch Platzhalter ersetzt, bevor ein Text ins Modell geht
- Optional: Bestehende Vorlagen sprachlich verbessern oder an unterschiedliche Schulzweige anpassen lassen

**Erwartetes Ergebnis:**
- Praxistaugliche Vorlagen und ein Bewusstsein für den notwendigen Anonymisierungsschritt
- Gemeinsame Diskussion: Welche Dokumenttypen im BBS-Betrieb eignen sich für LLM-Unterstützung, welche nicht?

### 5) Ergebnis-Review und Abschluss (20-30 min)
- Kurze Vorstellung der Gruppen-Ergebnisse
- Was hat gut funktioniert, wo waren Hürden?
- Best Practices für den Alltag
- Nächste Schritte im Team

## Benötigte Vorbereitung

### Organisatorisch
- Raum/Setup oder Remote-Tooling
- Gruppenaufteilung (2-4 Personen pro Gruppe)
- Vorab-Kommunikation zu benötigter Hardware

### Technisch
- Lokales LLM-Tool installiert (z. B. [Ollama](https://ollama.com) oder [LM Studio](https://lmstudio.ai))
- Mindestens ein vorab geladenes Modell, Empfehlungen:
  - **Einstieg:** `llama3.2:3b` oder `phi3:mini` (klein, schnell, läuft auf CPU)
  - **Standard:** `llama3.1:8b` oder `mistral:7b` (gute Balance aus Qualität und Geschwindigkeit)
  - **Leistungsstark (GPU):** `llama3.1:70b` oder `qwen2.5:32b`
- Testprompt vor dem Workshop erfolgreich ausgeführt
- Beispielmaterialien (Texte/Code) vorbereitet und lokal gespeichert

## Materialien
- Präsentationsfolien (Überblicksteil)
- Aufgabenblatt mit den 2-3 Praxisbeispielen
- Prompt-Cheatsheet (Rollen, Ziele, Einschränkungen, Ausgabeformat)
- Ergebnisvorlage für die Gruppenarbeit

## Didaktische Hinweise
- Mit leichtem Beispiel starten, dann Komplexität erhöhen
- Zeitboxen klar setzen und sichtbar machen
- Bei heterogenen Vorkenntnissen optionale Zusatzaufgaben anbieten
- Fokus auf Transfer in den Arbeitsalltag

## Optionale Erweiterungen (bei verbleibendem Zeitpuffer)
- Mini-Block zu Prompt-Evaluation
- Kurze Einführung in lokale RAG-Konzepte
- Vergleich von zwei lokalen Modellen anhand derselben Aufgabe

## Erfolgskriterien
Der Workshop war erfolgreich, wenn:
- die Teilnehmenden mindestens 2 Praxisbeispiele eigenständig abgeschlossen haben,
- Unterschiede zwischen lokalem und Cloud-basiertem Einsatz benennen können,
- ein realistisches Bild zu Aufwand, Nutzen und Grenzen mitnehmen.
