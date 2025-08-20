# Anhang D: KI-unterstützte Governance und Verifikation für sicheres Codieren

## Zielsetzung

Dieses Kapitel definiert grundlegende organisatorische Kontrollen für die sichere und effektive Nutzung von KI-unterstützten Codierungstools während der Softwareentwicklung und gewährleistet Sicherheit und Rückverfolgbarkeit im gesamten Softwareentwicklungslebenszyklus (SDLC).

---

## AD.1 KI-unterstützter sicherer Programmier-Workflow

Integrieren Sie KI-Werkzeuge in den sicheren Softwareentwicklungszyklus (SSDLC) der Organisation, ohne die bestehenden Sicherheitsbarrieren zu schwächen.

|   #    | Beschreibung                                                                                                                                                             | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AD.1.1 | Stellen Sie sicher, dass ein dokumentierter Arbeitsablauf beschreibt, wann und wie KI-Tools Code generieren, refaktorisieren oder überprüfen dürfen.                     |   1   |  D/V  |
| AD.1.2 | Überprüfen Sie, ob der Workflow jeder SSDLC-Phase (Design, Implementierung, Code-Review, Test, Bereitstellung) zugeordnet ist.                                           |   2   |   D   |
| AD.1.3 | Überprüfen Sie, ob Metriken (z. B. Verwundbarkeitsdichte, mittlere Erkennungszeit) für KI-erstellten Code erfasst und mit menschlichen Ausgangswerten verglichen werden. |   3   |  D/V  |

---

## AD.2 KI-Werkzeugqualifizierung & Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Codierwerkzeuge vor der Einführung auf Sicherheitsfunktionen, Risiken und Auswirkungen auf die Lieferkette bewertet werden.

|   #    | Beschreibung                                                                                                                                                                                                   | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.2.1 | Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI-Tool Missbrauch, Modellinversion, Datenleck und Abhängigkeitskettenrisiken identifiziert.                                                           |   1   |  D/V  |
| AD.2.2 | Stellen Sie sicher, dass die Toolbewertungen statische/dynamische Analysen aller lokalen Komponenten sowie die Bewertung von SaaS-Endpunkten (TLS, Authentifizierung/Autorisierung, Protokollierung) umfassen. |   2   |   D   |
| AD.2.3 | Stellen Sie sicher, dass Bewertungen einem anerkannten Rahmenwerk folgen und nach größeren Versionsänderungen erneut durchgeführt werden.                                                                      |   3   |  D/V  |

---

## AD.3 Sicheres Prompt- und Kontextmanagement

Verhindern Sie das Lecken von Geheimnissen, proprietärem Code und persönlichen Daten beim Erstellen von Aufforderungen oder Kontexten für KI-Modelle.

|   #    | Beschreibung                                                                                                                                                                                                   | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.3.1 | Verifizieren Sie, dass schriftliche Anweisungen das Senden von Geheimnissen, Zugangsdaten oder klassifizierten Daten in Eingabeaufforderungen verbieten.                                                       |   1   |  D/V  |
| AD.3.2 | Überprüfen Sie, dass technische Kontrollen (clientseitige Redaktion, genehmigte Kontextfilter) automatisch sensible Artefakte entfernen.                                                                       |   2   |   D   |
| AD.3.3 | Überprüfen Sie, dass Eingabeaufforderungen und Antworten tokenisiert, während der Übertragung und im Ruhezustand verschlüsselt sind und die Aufbewahrungsfristen der Datenklassifizierungspolitik entsprechen. |   3   |  D/V  |

---

## AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von durch KI-Ergebnisse eingeführten Schwachstellen, bevor der Code zusammengeführt oder bereitgestellt wird.

|   #    | Beschreibung                                                                                                                                                                                | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.4.1 | Stellen Sie sicher, dass von KI generierter Code stets einer menschlichen Codeüberprüfung unterzogen wird.                                                                                  |   1   |  D/V  |
| AD.4.2 | Stellen Sie sicher, dass automatisierte Scanner (SAST/IAST/DAST) bei jedem Pull Request mit KI-generiertem Code ausgeführt werden und Zusammenführungen bei kritischen Befunden blockieren. |   2   |   D   |
| AD.4.3 | Überprüfen Sie, dass Differential-Fuzz-Tests oder eigenschaftsbasierte Tests sicherheitskritische Verhaltensweisen nachweisen (z. B. Eingabevalidierung, Autorisierungslogik).              |   3   |  D/V  |

---

## AD.5 Erklärbarkeit & Nachverfolgbarkeit von Code-Vorschlägen

Geben Sie Prüfern und Entwicklern Einblick darin, warum eine Empfehlung gemacht wurde und wie sie sich entwickelt hat.

|   #    | Beschreibung                                                                                                                                                                                                         | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.5.1 | Überprüfen Sie, ob Prompt-/Antwortpaare mit Commit-IDs protokolliert werden.                                                                                                                                         |   1   |  D/V  |
| AD.5.2 | Überprüfen Sie, ob Entwickler Modellzitate (Trainingsausschnitte, Dokumentation) anzeigen können, die eine Empfehlung unterstützen.                                                                                  |   2   |   D   |
| AD.5.3 | Stellen Sie sicher, dass Erklärbarkeitsberichte zusammen mit Design-Artefakten gespeichert und in Sicherheitsüberprüfungen referenziert werden, um die Rückverfolgbarkeitsprinzipien nach ISO/IEC 42001 zu erfüllen. |   3   |  D/V  |

---

## AD.6 Kontinuierliches Feedback & Modell-Feinabstimmung

Verbessern Sie die Sicherheitsleistung des Modells im Laufe der Zeit und verhindern Sie gleichzeitig negative Drift.

|   #    | Beschreibung                                                                                                                                                                                                                           | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.6.1 | Verifizieren Sie, dass Entwickler unsichere oder nicht konforme Vorschläge markieren können und dass diese Markierungen verfolgt werden.                                                                                               |   1   |  D/V  |
| AD.6.2 | Verifizieren Sie, dass aggregiertes Feedback periodisch für Feinabstimmungen oder retrieval-unterstützte Generierung mit geprüften sicheren Codierungs-Korpora (z. B. OWASP Cheat Sheets) verwendet wird.                              |   2   |   D   |
| AD.6.3 | Verifizieren Sie, dass ein Closed-Loop-Evaluations-Framework nach jeder Feinabstimmung Regressionstests durchführt; Sicherheitsmetriken müssen vor der Bereitstellung mindestens die vorherigen Basiswerte erreichen oder übertreffen. |   3   |  D/V  |

---

### Referenzen

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

