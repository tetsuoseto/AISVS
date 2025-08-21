# Anhang D: KI-gestützte Governance und Verifikation sicherer Programmierung

## Zielsetzung

Dieses Kapitel definiert grundlegende organisatorische Kontrollmaßnahmen für den sicheren und effektiven Einsatz von KI-unterstützten Codierwerkzeugen während der Softwareentwicklung und stellt dabei Sicherheit und Nachvollziehbarkeit über den gesamten Softwareentwicklungszyklus (SDLC) sicher.

---

## AD.1 KI-gestützter Secure-Coding-Workflow

Integrieren Sie KI-Tools in den sicheren Software-Entwicklungszyklus (SSDLC) der Organisation, ohne bestehende Sicherheitskontrollen zu schwächen.

|   #    | Beschreibung                                                                                                                                                                                        | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.1.1 | Überprüfen Sie, ob ein dokumentierter Workflow beschreibt, wann und wie KI-Tools Code generieren, refaktorisieren oder überprüfen dürfen.                                                           |   1   |  D/V  |
| AD.1.2 | Überprüfen Sie, ob der Workflow jeder SSDLC-Phase zugeordnet ist (Design, Implementierung, Code-Review, Testen, Bereitstellung).                                                                    |   2   |   D   |
| AD.1.3 | Stellen Sie sicher, dass Metriken (z. B. Verwundbarkeitsdichte, mittlere Erkennungszeit) für KI-erzeugten Code erfasst und mit den Basiswerten ausschließlich menschlichen Codes verglichen werden. |   3   |  D/V  |

---

## AD.2 KI-Werkzeugqualifizierung & Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Codierungswerkzeuge vor der Einführung auf Sicherheitsfunktionen, Risiken und Auswirkungen auf die Lieferkette bewertet werden.

|   #    | Beschreibung                                                                                                                                                                                                | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.2.1 | Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI-Werkzeug Missbrauch, Modellinversion, Datenleck und Risiken der Abhängigkeitskette identifiziert.                                                |   1   |  D/V  |
| AD.2.2 | Überprüfen Sie, dass die Tool-Bewertungen statische/dynamische Analysen aller lokalen Komponenten sowie die Bewertung von SaaS-Endpunkten (TLS, Authentifizierung/Autorisierung, Protokollierung) umfassen. |   2   |   D   |
| AD.2.3 | Stellen Sie sicher, dass Bewertungen einem anerkannten Rahmenwerk folgen und nach größeren Versionsänderungen erneut durchgeführt werden.                                                                   |   3   |  D/V  |

---

## AD.3 Sichere Eingabeaufforderungs- und Kontextverwaltung

Verhindern Sie das Austreten von Geheimnissen, firmeneigenem Code und persönlichen Daten beim Erstellen von Prompts oder Kontexten für KI-Modelle.

|   #    | Beschreibung                                                                                                                                                                                                                 | Ebene | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.3.1 | Stellen Sie sicher, dass schriftliche Anweisungen das Senden von Geheimnissen, Anmeldeinformationen oder klassifizierten Daten in Eingabeaufforderungen verboten.                                                            |   1   |  D/V  |
| AD.3.2 | Überprüfen Sie, dass technische Kontrollen (clientseitige Schwärzung, genehmigte Kontextfilter) automatisch sensible Artefakte entfernen.                                                                                    |   2   |   D   |
| AD.3.3 | Stellen Sie sicher, dass Eingabeaufforderungen und Antworten tokenisiert, während der Übertragung und im Ruhezustand verschlüsselt sind und die Aufbewahrungsfristen mit der Datenklassifizierungsrichtlinie übereinstimmen. |   3   |  D/V  |

---

## AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von Schwachstellen, die durch KI-Ausgaben eingeführt wurden, bevor der Code zusammengeführt oder bereitgestellt wird.

|   #    | Beschreibung                                                                                                                                                                                | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.4.1 | Stellen Sie sicher, dass KI-generierter Code immer einer menschlichen Codeüberprüfung unterzogen wird.                                                                                      |   1   |  D/V  |
| AD.4.2 | Stellen Sie sicher, dass automatisierte Scanner (SAST/IAST/DAST) bei jedem Pull Request mit KI-generiertem Code ausgeführt werden und Zusammenführungen bei kritischen Befunden blockieren. |   2   |   D   |
| AD.4.3 | Verifizieren Sie, dass Differenzial-Fuzz-Tests oder eigenschaftsbasierte Tests sicherheitskritische Verhaltensweisen (z. B. Eingabevalidierung, Autorisierungslogik) nachweisen.            |   3   |  D/V  |

---

## AD.5 Erklärbarkeit und Rückverfolgbarkeit von Code-Vorschlägen

Geben Sie Prüfern und Entwicklern Einblick, warum ein Vorschlag gemacht wurde und wie er sich entwickelt hat.

|   #    | Beschreibung                                                                                                                                                                                                   | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.5.1 | Überprüfen Sie, ob Prompt/Antwort-Paare mit Commit-IDs protokolliert werden.                                                                                                                                   |   1   |  D/V  |
| AD.5.2 | Stellen Sie sicher, dass Entwickler Modellzitate (Trainingsausschnitte, Dokumentation) anzeigen können, die eine Vorschlag unterstützen.                                                                       |   2   |   D   |
| AD.5.3 | Überprüfen Sie, dass Erklärbarkeitsberichte zusammen mit Designartefakten gespeichert und in Sicherheitsüberprüfungen referenziert werden, um die Rückverfolgbarkeitsprinzipien von ISO/IEC 42001 zu erfüllen. |   3   |  D/V  |

---

## AD.6 Kontinuierliches Feedback & Modell-Feinabstimmung

Verbessern Sie die Sicherheit der Modellleistung im Laufe der Zeit und verhindern Sie gleichzeitig negative Abweichungen.

|   #    | Beschreibung                                                                                                                                                                                                                        | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.6.1 | Stellen Sie sicher, dass Entwickler unsichere oder nicht konforme Vorschläge markieren können und dass diese Markierungen nachverfolgt werden.                                                                                      |   1   |  D/V  |
| AD.6.2 | Stellen Sie sicher, dass aggregiertes Feedback die periodische Feinabstimmung oder retrieval-gestützte Generierung mit geprüften sicheren Codierkorpora (z. B. OWASP Cheat Sheets) informiert.                                      |   2   |   D   |
| AD.6.3 | Stellen Sie sicher, dass ein Closed-Loop-Bewertungsharness nach jeder Feinabstimmung Regressionstests durchführt; Sicherheitsmetriken müssen vor der Bereitstellung mindestens die vorherigen Baselines erreichen oder übertreffen. |   3   |  D/V  |

---

### Literaturverzeichnis

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

