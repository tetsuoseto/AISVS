# C5 Zugriffskontrolle und Identität für KI-Komponenten und Benutzer

## Kontrollziel

Effektive Zugriffskontrolle für KI-Systeme erfordert ein robustes Identitätsmanagement, kontextbewusste Autorisierung und Laufzeitdurchsetzung gemäß Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten nur mit Modellen, Daten und Rechenressourcen innerhalb ausdrücklich gewährter Bereiche interagieren, mit kontinuierlicher Überprüfung und Auditmöglichkeiten.

---

## C5.1 Identitätsverwaltung & Authentifizierung

Richten Sie kryptografisch gesicherte Identitäten für alle Entitäten ein, mit Multi-Faktor-Authentifizierung für privilegierte Operationen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                  | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.1.1 | Stellen Sie sicher, dass alle menschlichen Benutzer und Dienstprinzipale sich über einen zentralisierten unternehmensweiten Identitätsanbieter (IdP) unter Verwendung der OIDC/SAML-Protokolle mit eindeutigen Identitäts-zu-Token-Zuordnungen authentifizieren (keine gemeinsamen Konten oder Zugangsdaten). |   1    |  D/V  |
| 5.1.2 | Stellen Sie sicher, dass bei risikoreichen Vorgängen (Modelldeployment, Gewichtsexport, Zugriff auf Trainingsdaten, Änderungen an Produktionskonfigurationen) Multi-Faktor-Authentifizierung oder Step-up-Authentifizierung mit Sitzungsnevalidierung erforderlich ist.                                       |   1    |  D/V  |
| 5.1.3 | Stellen Sie sicher, dass neue Verantwortliche eine Identitätsprüfung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugang zu Produktionssystemen erhalten.                                                                                                  |   2    |   D   |
| 5.1.4 | Stellen Sie sicher, dass Zugriffsüberprüfungen vierteljährlich durchgeführt werden, mit automatischer Erkennung inaktiver Konten, Durchsetzung der Anmeldeinformationsrotation und Workflows zur De-Provisionierung.                                                                                          |   2    |   V   |
| 5.1.5 | Stellen Sie sicher, dass föderierte KI-Agenten sich über signierte JWT-Assertions authentifizieren, die eine maximale Laufzeit von 24 Stunden haben und einen kryptografischen Herkunftsnachweis enthalten.                                                                                                   |   3    |  D/V  |

---

## C5.2 Ressourcenautorisierung & Prinzip der minimalen Rechte

Implementieren Sie fein abgestufte Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Prüfpfaden.

|   #   | Beschreibung                                                                                                                                                                                                                                                                       | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.2.1 | Stellen Sie sicher, dass jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Recheninstanzen) rollenbasierte Zugriffskontrollen mit expliziten Erlaubnislisten und Standard-Ablehnungsrichtlinien durchsetzt.                                 |   1    |  D/V  |
| 5.2.2 | Stellen Sie sicher, dass die Prinzipien der geringsten Privilegien standardmäßig bei Dienstkonten durchgesetzt werden, beginnend mit Lesezugriffsrechten, und dass für Schreibzugriffe eine dokumentierte geschäftliche Begründung erforderlich ist.                               |   1    |  D/V  |
| 5.2.3 | Überprüfen Sie, ob alle Änderungen der Zugriffskontrolle mit genehmigten Änderungsanforderungen verknüpft und unveränderlich protokolliert sind, einschließlich Zeitstempel, Akteur-Identitäten, Ressourcenkennungen und Berechtigungsdifferenzen.                                 |   1    |   V   |
| 5.2.4 | Stellen Sie sicher, dass Datenklassifizierungskennzeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Embeddings, Prompt-Caches, Modellausgaben) übertragen werden und eine konsistente Durchsetzung der Richtlinien gewährleistet ist. |   2    |   D   |
| 5.2.5 | Überprüfen Sie, ob unautorisierte Zugriffsversuche und Privilegienerhöhungen Echtzeitwarnungen mit kontextbezogenen Metadaten an SIEM-Systeme innerhalb von 5 Minuten auslösen.                                                                                                    |   2    |  D/V  |

---

## C5.3 Dynamische Richtlinienbewertung

Setzen Sie attributbasierte Zugriffskontrollmotoren (ABAC) für kontextbewusste Autorisierungsentscheidungen mit Prüfungsfunktionen ein.

|   #   | Beschreibung                                                                                                                                                                                                                         | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 5.3.1 | Stellen Sie sicher, dass Autorisierungsentscheidungen an eine dedizierte Richtlinien-Engine (OPA, Cedar oder vergleichbar) ausgelagert werden, die über authentifizierte APIs mit kryptografischem Integritätsschutz zugänglich ist. |   1    |  D/V  |
| 5.3.2 | Überprüfen Sie, dass Richtlinien dynamische Attribute zur Laufzeit auswerten, einschließlich Benutzerfreigabestufe, Ressourcensensitivitätsklassifikation, Anforderungskontext, Mandantenisolation und zeitlichen Beschränkungen.    |   1    |  D/V  |
| 5.3.3 | Stellen Sie sicher, dass Richtliniendefinitionen versioniert, von Kollegen überprüft und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in der Produktion bereitgestellt werden.                          |   2    |   D   |
| 5.3.4 | Überprüfen Sie, ob die Ergebnisse der Policy-Auswertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übermittelt werden.                           |   2    |   V   |
| 5.3.5 | Überprüfen Sie, dass die Zeitüberschreitungswerte (TTL) des Richtlinien-Caches für hochsensible Ressourcen 5 Minuten und für Standardressourcen mit Cache-Invalidierungsmöglichkeiten 1 Stunde nicht überschreiten.                  |   3    |  D/V  |

---

## C5.4 Sicherheitsdurchsetzung zur Abfragezeit

Implementieren Sie Sicherheitskontrollen auf Datenbankebene mit obligatorischer Filterung und Richtlinien für Zeilenebenen-Sicherheit.

|   #   | Beschreibung                                                                                                                                                                                                                                                   | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.4.1 | Überprüfen Sie, dass alle Vektor-Datenbank- und SQL-Abfragen obligatorische Sicherheitsfilter (Mandanten-ID, Sensitivitätskennzeichnungen, Benutzerbereich) enthalten, die auf der Ebene der Datenbank-Engine durchgesetzt werden und nicht im Anwendungscode. |   1    |  D/V  |
| 5.4.2 | Stellen Sie sicher, dass zeilenbasierte Sicherheitsrichtlinien (RLS) und feldbasierte Maskierung mit Richtlinienvererbung für alle Vektordatenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.                                                      |   1    |  D/V  |
| 5.4.3 | Stellen Sie sicher, dass fehlgeschlagene Autorisierungsprüfungen "Confused Deputy-Angriffe" verhindern, indem sie Abfragen sofort abbrechen und explizite Autorisierungsfehlercodes zurückgeben, anstatt leere Ergebnismengen zu liefern.                      |   2    |   D   |
| 5.4.4 | Stellen Sie sicher, dass die Latenzzeit der Richtlinienbewertung kontinuierlich überwacht wird und automatisierte Warnungen bei Zeitüberschreitungen ausgelöst werden, die eine Umgehung der Autorisierung ermöglichen könnten.                                |   2    |   V   |
| 5.4.5 | Überprüfen Sie, ob Abfrage-Wiederholungsmechanismen Autorisierungsrichtlinien neu bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.                                                                      |   3    |  D/V  |

---

## C5.5 Ausgabe-Filterung & Datenschutzmaßnahmen

Implementieren Sie Nachbearbeitungskontrollen, um die unbefugte Offenlegung von Daten in KI-generierten Inhalten zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.5.1 | Stellen Sie sicher, dass Post-Inferenz-Filtermechanismen unautorisierte PII, klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anforderer geliefert werden.        |   1    |  D/V  |
| 5.5.2 | Stellen Sie sicher, dass Zitate, Referenzen und Quellenangaben in Modellausgaben gegen die Berechtigungen des Aufrufers überprüft und entfernt werden, wenn ein unautorisierter Zugriff festgestellt wird.  |   1    |  D/V  |
| 5.5.3 | Überprüfen Sie, ob Ausgabeformatbeschränkungen (bereinigte PDFs, metadatenfreie Bilder, genehmigte Dateitypen) basierend auf Benutzerberechtigungsstufen und Datenklassifizierungen durchgesetzt werden.    |   2    |   D   |
| 5.5.4 | Stellen Sie sicher, dass Schwärzungsalgorithmen deterministisch, versionskontrolliert sind und Prüfprotokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.                |   2    |   V   |
| 5.5.5 | Überprüfen Sie, dass hochriskante Schwärzungsereignisse adaptive Protokolle erzeugen, die kryptografische Hashes des Originalinhalts für die forensische Wiederherstellung ohne Datenoffenlegung enthalten. |   3    |   V   |

---

## C5.6 Mandanten-Isolierung

Sorgen Sie für kryptografische und logische Isolation zwischen Mietern in gemeinsamer KI-Infrastruktur.

|   #   | Beschreibung                                                                                                                                                                                                                | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.6.1 | Stellen Sie sicher, dass Speicherbereiche, Einbettungsspeicher, Cache-Einträge und temporäre Dateien pro Mandant namespace-getrennt sind und bei Löschung des Mandanten oder Beendigung der Sitzung sicher gelöscht werden. |   1    |  D/V  |
| 5.6.2 | Stellen Sie sicher, dass jede API-Anfrage einen authentifizierten Mandantenbezeichner enthält, der kryptographisch gegen den Sitzungskontext und die Benutzerberechtigungen validiert wird.                                 |   1    |  D/V  |
| 5.6.3 | Überprüfen Sie, ob Netzwerkrichtlinien Standard-Verweigerungsregeln für die Kommunikation zwischen Mandanten innerhalb von Service-Meshes und Container-Orchestrierungsplattformen implementieren.                          |   2    |   D   |
| 5.6.4 | Überprüfen Sie, dass Verschlüsselungsschlüssel pro Mandant eindeutig sind, mit Unterstützung für kundenverwaltete Schlüssel (CMK) und kryptografischer Isolation zwischen den Datenspeichern der Mandanten.                 |   3    |   D   |

---

## C5.7 Autonome Agenten-Autorisierung

Steuern Sie Berechtigungen für KI-Agenten und autonome Systeme durch segmentierte Fähigkeitstoken und kontinuierliche Autorisierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                            | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.7.1 | Überprüfen Sie, dass autonome Agenten scopespezifische Fähigkeitstoken erhalten, die ausdrücklich die erlaubten Aktionen, zugänglichen Ressourcen, Zeitgrenzen und betrieblichen Einschränkungen auflisten.                                                             |   1    |  D/V  |
| 5.7.2 | Stellen Sie sicher, dass risikoreiche Funktionen (Dateisystemzugriff, Codeausführung, externe API-Aufrufe, finanzielle Transaktionen) standardmäßig deaktiviert sind und eine explizite Autorisierung zur Aktivierung mit geschäftlichen Begründungen erforderlich ist. |   1    |  D/V  |
| 5.7.3 | Überprüfen Sie, dass Zugriffstoken an Benutzersitzungen gebunden sind, eine kryptografische Integritätssicherung enthalten und sicherstellen, dass sie nicht offline gespeichert oder wiederverwendet werden können.                                                    |   2    |   D   |
| 5.7.4 | Stellen Sie sicher, dass von Agenten initiierte Aktionen einer sekundären Autorisierung durch die ABAC-Richtlinien-Engine unterzogen werden, mit vollständiger Kontextbewertung und Prüfprotokollierung.                                                                |   2    |   V   |
| 5.7.5 | Stellen Sie sicher, dass Agentenfehlerbedingungen und Ausnahmebehandlungen Informationen zum Fähigkeitsumfang enthalten, um die Vorfallanalyse und forensische Untersuchung zu unterstützen.                                                                            |   3    |   V   |

---

## Referenzen

### Standards & Rahmenwerke

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Implementierungsanleitungen

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### KI-spezifische Sicherheit

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

