# Anhang D: KI-gestützte sichere Codierungs-Governance und Verifikation

## Ziel

Dieses Kapitel definiert grundlegende organisatorische Kontrollen für den sicheren und effektiven Einsatz von KI-unterstützten Codierungstools während der Softwareentwicklung, um Sicherheit und Nachvollziehbarkeit über den SDLC hinweg zu gewährleisten.

---

## KI-gestützter sicherer Codierungs-Workflow

Integrieren Sie KI-Werkzeuge in den sicheren Software-Entwicklungslebenszyklus der Organisation (SSDLC), ohne die bestehenden Sicherheitsbarrieren zu schwächen.

|   #    | Beschreibung                                                                                                                                                                                  | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.1.1 | Stellen Sie sicher, dass ein dokumentierter Workflow beschreibt, wann und wie KI-Werkzeuge Code erzeugen, refaktorisieren oder überprüfen dürfen.                                             |   1   |  D/V  |
| AD.1.2 | Überprüfen Sie, ob der Workflow jeder SSDLC-Phase zugeordnet ist (Design, Implementierung, Code-Review, Tests, Bereitstellung).                                                               |   2   |   D   |
| AD.1.3 | Verifizieren Sie, dass Metriken (z. B. Verwundbarkeitsdichte, mean‑time‑to‑detect) bei von KI erzeugtem Code erhoben und mit Baselines verglichen werden, die ausschließlich menschlich sind. |   3   |  D/V  |

---

## AD.2 KI-Tool-Qualifikation und Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Programmierwerkzeuge hinsichtlich Sicherheitsfunktionen, Risiken und Auswirkungen der Lieferkette vor der Einführung bewertet werden.

|   #    | Beschreibung                                                                                                                                                                                                   | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.2.1 | Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI‑Tool Missbrauch, Modell‑Inversion, Datenleck und Abhängigkeitskettenrisiken identifiziert.                                                          |   1   |  D/V  |
| AD.2.2 | Stellen Sie sicher, dass Toolbewertungen eine statische/dynamische Analyse aller lokalen Komponenten sowie eine Bewertung der SaaS-Endpunkte (TLS, Authentifizierung/Autorisierung, Protokollierung) umfassen. |   2   |   D   |
| AD.2.3 | Vergewissern Sie sich, dass Evaluierungen einem anerkannten Rahmenwerk folgen und nach größeren Versionsänderungen erneut durchgeführt werden.                                                                 |   3   |  D/V  |

---

## AD.3 Sichere Prompt- und Kontextverwaltung

Verhindern Sie das Offenlegen von Geheimnissen, proprietärem Code und personenbezogenen Daten beim Erstellen von Prompts oder Kontexten für KI-Modelle.

|   #    | Beschreibung                                                                                                                                                                                                               | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.3.1 | Überprüfen Sie, ob die schriftlichen Richtlinien das Senden von Geheimnissen, Anmeldeinformationen oder klassifizierten Daten in Eingabeaufforderungen verbieten.                                                          |   1   |  D/V  |
| AD.3.2 | Überprüfen Sie, ob technische Kontrollen (client‑seitige Schwärzung, genehmigte Kontextfilter) automatisch sensible Artefakte entfernen.                                                                                   |   2   |   D   |
| AD.3.3 | Überprüfen Sie, dass Eingabeaufforderungen und Antworten tokenisiert sind, während der Übertragung und im Ruhezustand verschlüsselt werden, und dass Aufbewahrungsfristen der Datenklassifizierungsrichtlinie entsprechen. |   3   |  D/V  |

---

## AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von Schwachstellen, die durch KI-Ausgaben eingeführt werden, bevor der Code zusammengeführt oder bereitgestellt wird.

|   #    | Beschreibung                                                                                                                                                                                     | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AD.4.1 | Stellen Sie sicher, dass KI-generierter Code stets einer menschlichen Codeüberprüfung unterzogen wird.                                                                                           |   1   |  D/V  |
| AD.4.2 | Stellen Sie sicher, dass automatische Scanner (SAST/IAST/DAST) bei jedem Pull Request ausgeführt werden, der AI-generierten Code enthält, und Merge-Vorgänge bei kritischen Befunden blockieren. |   2   |   D   |
| AD.4.3 | Überprüfen Sie, dass Differential-Fuzzing oder Eigenschaftsbasierte Tests sicherheitsrelevante Verhaltensweisen (z. B. Eingabevalidierung, Autorisierungslogik) nachweisen.                      |   3   |  D/V  |

---

## AD.5 Erklärbarkeit & Rückverfolgbarkeit von Codevorschlägen

Auditoren und Entwickler erhalten Einblick, warum ein Vorschlag gemacht wurde und wie er sich entwickelt hat.

|   #    | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.5.1 | Überprüfen Sie, ob Prompt-/Antwort-Paare mit Commit-IDs protokolliert werden.                                                                                                                                               |   1   |  D/V  |
| AD.5.2 | Stellen Sie sicher, dass Entwickler Modellquellenangaben (Trainingsauszüge, Dokumentation) bereitstellen können, die eine Empfehlung unterstützen.                                                                          |   2   |   D   |
| AD.5.3 | Überprüfen Sie, dass Berichte zur Erklärbarkeit zusammen mit Designartefakten gespeichert werden und in Sicherheitsprüfungen referenziert werden, um die Prinzipien der Nachverfolgbarkeit gemäß ISO/IEC 42001 zu erfüllen. |   3   |  D/V  |

---

## AD.6 Kontinuierliches Feedback und Modell Fein‑Tuning

Die Sicherheitsleistung des Modells im Laufe der Zeit verbessern und gleichzeitig negativen Drift verhindern.

|   #    | Beschreibung                                                                                                                                                                                                                             | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.6.1 | Überprüfen Sie, dass Entwickler unsichere oder nicht‑konforme Vorschläge kennzeichnen können, und dass diese Kennzeichnungen nachverfolgt werden.                                                                                        |   1   |  D/V  |
| AD.6.2 | Stellen Sie sicher, dass aggregiertes Feedback die regelmäßige Fein‑Abstimmung oder Abruf‑ergänzte Generierung mit geprüften sicheren Codierungs‑Korpora unterstützt (z. B. OWASP Cheat Sheets).                                         |   2   |   D   |
| AD.6.3 | Überprüfen Sie, dass ein Closed‑Loop‑Evaluierungs‑Harness nach jeder Fein‑abstimmung Regressionstests durchführt; Sicherheitskennzahlen müssen die vorherigen Referenzwerte erfüllen oder übertreffen, bevor die Bereitstellung erfolgt. |   3   |  D/V  |

---

### Referenzen

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

