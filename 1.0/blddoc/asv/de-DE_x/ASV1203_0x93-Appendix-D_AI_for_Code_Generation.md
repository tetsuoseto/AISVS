# Anhang D: KI-gestützte Governance und Verifizierung sicherer Codierung

## Zielsetzung

Dieses Kapitel definiert grundlegende organisatorische Kontrollen für die sichere und effektive Nutzung von KI-gestützten Codierwerkzeugen während der Softwareentwicklung und gewährleistet Sicherheit und Rückverfolgbarkeit über den gesamten SDLC.

---

## AD.1 KI-unterstützter Secure-Coding-Workflow

Integrieren Sie KI-Tools in den sicheren Software-Entwicklungszyklus (SSDLC) der Organisation, ohne die bestehenden Sicherheitsschranken zu schwächen.

|   #    | Beschreibung                                                                                                                                                                        | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.1.1 | Stellen Sie sicher, dass ein dokumentierter Arbeitsablauf beschreibt, wann und wie KI-Tools Code erzeugen, überarbeiten oder überprüfen dürfen.                                     |   1    |  D/V  |
| AD.1.2 | Überprüfen Sie, ob der Arbeitsablauf jeder SSDLC-Phase zugeordnet ist (Design, Implementierung, Code-Review, Testen, Bereitstellung).                                               |   2    |   D   |
| AD.1.3 | Überprüfen Sie, ob Metriken (z. B. Verwundbarkeitsdichte, mittlere Zeit bis zur Erkennung) für KI-generierten Code erfasst und mit rein menschlichen Basiswerten verglichen werden. |   3    |  D/V  |

---

## AD.2 KI-Werkzeugqualifizierung & Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Codierwerkzeuge vor der Einführung hinsichtlich Sicherheitsfähigkeiten, Risiken und Auswirkungen auf die Lieferkette bewertet werden.

|   #    | Beschreibung                                                                                                                                                                                                          | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.2.1 | Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI-Tool Missbrauch, Modell-Inversion, Datenleckage und Risiken in der Abhängigkeitskette identifiziert.                                                       |   1    |  D/V  |
| AD.2.2 | Stellen Sie sicher, dass die Bewertung der Tools eine statische/dynamische Analyse aller lokalen Komponenten sowie eine Bewertung der SaaS-Endpunkte (TLS, Authentifizierung/Autorisierung, Protokollierung) umfasst. |   2    |   D   |
| AD.2.3 | Stellen Sie sicher, dass Bewertungen einem anerkannten Rahmenwerk folgen und nach größeren Versionsänderungen erneut durchgeführt werden.                                                                             |   3    |  D/V  |

---

## AD.3 Sichere Verwaltung von Eingabeaufforderungen und Kontext

Verhindern Sie das Leaken von Geheimnissen, proprietärem Code und persönlichen Daten beim Erstellen von Eingabeaufforderungen oder Kontexten für KI-Modelle.

|   #    | Beschreibung                                                                                                                                                                                                       | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| AD.3.1 | Überprüfen Sie, ob die schriftlichen Richtlinien das Senden von Geheimnissen, Zugangsdaten oder klassifizierten Daten in Eingabeaufforderungen untersagen.                                                         |   1    |  D/V  |
| AD.3.2 | Überprüfen Sie, ob technische Kontrollen (Client-seitige Schwärzung, genehmigte Kontextfilter) automatisch sensible Artefakte entfernen.                                                                           |   2    |   D   |
| AD.3.3 | Überprüfen Sie, dass Eingabeaufforderungen und Antworten tokenisiert, während der Übertragung und im Ruhezustand verschlüsselt sind und die Aufbewahrungsfristen den Datenklassifizierungsrichtlinien entsprechen. |   3    |  D/V  |

---

## AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von Schwachstellen, die durch AI-Ausgaben eingeführt wurden, bevor der Code zusammengeführt oder bereitgestellt wird.

|   #    | Beschreibung                                                                                                                                                                                   | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.4.1 | Stellen Sie sicher, dass KI-generierter Code stets einer menschlichen Codeüberprüfung unterzogen wird.                                                                                         |   1    |  D/V  |
| AD.4.2 | Stellen Sie sicher, dass automatisierte Scanner (SAST/IAST/DAST) bei jedem Pull Request mit KI-generiertem Code ausgeführt werden und Zusammenführungen bei kritischen Ergebnissen blockieren. |   2    |   D   |
| AD.4.3 | Überprüfen Sie, dass differentialer Fuzz-Testing oder eigenschaftsbasierte Tests sicherheitskritische Verhaltensweisen nachweisen (z. B. Eingabevalidierung, Autorisierungslogik).             |   3    |  D/V  |

---

## AD.5 Erklärbarkeit und Nachverfolgbarkeit von Code-Vorschlägen

Bieten Sie Prüfern und Entwicklern Einblick darin, warum ein Vorschlag gemacht wurde und wie er sich entwickelt hat.

|   #    | Beschreibung                                                                                                                                                                                                        | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.5.1 | Überprüfen Sie, ob Eingabeaufforderungs-/Antwortpaare mit Commit-IDs protokolliert werden.                                                                                                                          |   1    |  D/V  |
| AD.5.2 | Überprüfen Sie, ob Entwickler Modellzitate (Trainingsausschnitte, Dokumentation) anzeigen können, die eine Empfehlung unterstützen.                                                                                 |   2    |   D   |
| AD.5.3 | Stellen Sie sicher, dass Erklärbarkeitsberichte zusammen mit Design-Artefakten gespeichert und in Sicherheitsüberprüfungen referenziert werden, um die Rückverfolgbarkeitsprinzipien der ISO/IEC 42001 zu erfüllen. |   3    |  D/V  |

---

## AD.6 Kontinuierliches Feedback & Modell-Feinabstimmung

Verbessern Sie die Sicherheitsleistung des Modells im Laufe der Zeit und verhindern Sie dabei Leistungsverschlechterungen.

|   #    | Beschreibung                                                                                                                                                                                                             | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| AD.6.1 | Überprüfen Sie, ob Entwickler unsichere oder nicht konforme Vorschläge markieren können und ob diese Markierungen nachverfolgt werden.                                                                                   |   1    |  D/V  |
| AD.6.2 | Stellen Sie sicher, dass aggregiertes Feedback die periodische Feinabstimmung oder die retrieval-ergänzte Generierung mit geprüften, sicherheitsorientierten Programmier-Korpora (z. B. OWASP Cheat Sheets) informiert.  |   2    |   D   |
| AD.6.3 | Verifizieren Sie, dass ein Closed-Loop-Evaluierungs-Framework nach jedem Fine-Tuning Regressionstests durchführt; Sicherheitsmetriken müssen vor der Bereitstellung die vorherigen Baselines erreichen oder übertreffen. |   3    |  D/V  |

---

### Referenzen

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

