# Anhang D: KI-gestützte Governance und Verifikation der sicheren Programmierung

## Zielsetzung

Dieses Kapitel definiert grundlegende organisatorische Kontrollen für die sichere und effektive Nutzung von KI-unterstützten Codierwerkzeugen während der Softwareentwicklung, um Sicherheit und Rückverfolgbarkeit über den gesamten SDLC hinweg zu gewährleisten.

---

## AD.1 KI-unterstützter Secure-Coding-Workflow

Integrieren Sie KI-Werkzeuge in den sicheren Software-Entwicklungslebenszyklus (SSDLC) der Organisation, ohne bestehende Sicherheitsbarrieren zu schwächen.

|   #    | Beschreibung                                                                                                                                                                               | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AD.1.1 | Überprüfen Sie, ob ein dokumentierter Workflow beschreibt, wann und wie KI-Tools Code generieren, umgestalten oder überprüfen dürfen.                                                      |   1   |  D/V  |
| AD.1.2 | Überprüfen Sie, ob der Workflow jeder SSDLC-Phase zugeordnet ist (Design, Implementierung, Code-Review, Testen, Bereitstellung).                                                           |   2   |   D   |
| AD.1.3 | Stellen Sie sicher, dass Metriken (z. B. Schwachstellendichte, mittlere Erkennungszeit) für KI-generierten Code erfasst und mit ausschließlich menschlichen Basiswerten verglichen werden. |   3   |  D/V  |

---

## AD.2 Qualifizierung von KI-Tools & Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Codierwerkzeuge vor der Einführung auf Sicherheitsfunktionen, Risiken und Auswirkungen auf die Lieferkette bewertet werden.

|   #    | Beschreibung                                                                                                                                                                                                  | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.2.1 | Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI-Werkzeug Missbrauch, Modell-Inversion, Datenleckage und Risiken in der Abhängigkeitskette identifiziert.                                           |   1   |  D/V  |
| AD.2.2 | Stellen Sie sicher, dass Tool-Evaluierungen statische/dynamische Analysen aller lokalen Komponenten sowie die Bewertung von SaaS-Endpunkten (TLS, Authentifizierung/Autorisierung, Protokollierung) umfassen. |   2   |   D   |
| AD.2.3 | Stellen Sie sicher, dass Bewertungen einem anerkannten Rahmenwerk folgen und nach großen Versionsänderungen erneut durchgeführt werden.                                                                       |   3   |  D/V  |

---

## AD.3 Sicheres Prompt- und Kontextmanagement

Verhindern Sie die Weitergabe von Geheimnissen, proprietärem Code und persönlichen Daten beim Erstellen von Eingabeaufforderungen oder Kontexten für KI-Modelle.

|   #    | Beschreibung                                                                                                                                                                                                          | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.3.1 | Stellen Sie sicher, dass schriftliche Anweisungen das Senden von Geheimnissen, Zugangsdaten oder klassifizierten Daten in Eingabeaufforderungen untersagen.                                                           |   1   |  D/V  |
| AD.3.2 | Überprüfen Sie, ob technische Kontrollen (clientseitige Schwärzung, genehmigte Kontextfilter) sensible Artefakte automatisch entfernen.                                                                               |   2   |   D   |
| AD.3.3 | Stellen Sie sicher, dass Eingabeaufforderungen und Antworten tokenisiert, während der Übertragung und im Ruhezustand verschlüsselt sind und die Aufbewahrungsfristen der Datenklassifizierungsrichtlinie entsprechen. |   3   |  D/V  |

---

## AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von Schwachstellen, die durch KI-Ausgaben eingeführt wurden, bevor der Code zusammengeführt oder bereitgestellt wird.

|   #    | Beschreibung                                                                                                                                                                                    | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.4.1 | Stellen Sie sicher, dass von KI generierter Code stets einer menschlichen Codeüberprüfung unterzogen wird.                                                                                      |   1   |  D/V  |
| AD.4.2 | Stellen Sie sicher, dass automatisierte Scanner (SAST/IAST/DAST) bei jedem Pull Request mit KI-generiertem Code ausgeführt werden und bei kritischen Ergebnissen das Zusammenführen blockieren. |   2   |   D   |
| AD.4.3 | Überprüfen Sie, ob differentielles Fuzz-Testing oder eigenschaftsbasierte Tests sicherheitskritische Verhaltensweisen (z. B. Eingabevalidierung, Autorisierungslogik) nachweisen.               |   3   |  D/V  |

---

## AD.5 Erklärbarkeit und Rückverfolgbarkeit von Code-Vorschlägen

Geben Sie Prüfern und Entwicklern Einblicke darüber, warum ein Vorschlag gemacht wurde und wie er sich entwickelt hat.

|   #    | Beschreibung                                                                                                                                                                                                       | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AD.5.1 | Überprüfen Sie, ob Aufforderungs-/Antwortpaare mit Commit-IDs protokolliert werden.                                                                                                                                |   1   |  D/V  |
| AD.5.2 | Überprüfen Sie, ob Entwickler Modellzitate (Trainingsausschnitte, Dokumentation) bereitstellen können, die eine Empfehlung unterstützen.                                                                           |   2   |   D   |
| AD.5.3 | Stellen Sie sicher, dass Erklärbarkeitsberichte zusammen mit Designartefakten gespeichert und in Sicherheitsüberprüfungen referenziert werden, um die Rückverfolgbarkeitsprinzipien der ISO/IEC 42001 zu erfüllen. |   3   |  D/V  |

---

## AD.6 Kontinuierliches Feedback & Modell-Feinabstimmung

Verbessern Sie die Sicherheitsleistung des Modells im Laufe der Zeit und verhindern Sie gleichzeitig negative Abweichungen.

|   #    | Beschreibung                                                                                                                                                                                                       | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AD.6.1 | Stellen Sie sicher, dass Entwickler unsichere oder nicht konforme Vorschläge markieren können und dass diese Markierungen nachverfolgt werden.                                                                     |   1   |  D/V  |
| AD.6.2 | Stellen Sie sicher, dass aggregiertes Feedback die periodische Feinabstimmung oder retrieval-unterstützte Generierung mit geprüften Secure-Coding-Korpora (z. B. OWASP Cheat Sheets) informiert.                   |   2   |   D   |
| AD.6.3 | Stellen Sie sicher, dass ein Closed-Loop-Evaluierungsharness nach jedem Fine-Tune Regressionsprüfungen durchführt; Sicherheitsmetriken müssen vor der Bereitstellung frühere Baselines erreichen oder übertreffen. |   3   |  D/V  |

---

### Referenzen

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

