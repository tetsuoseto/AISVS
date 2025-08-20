# C5 Zugriffskontrolle & Identität für KI-Komponenten & Benutzer

## Kontrollziel

Effektive Zugriffskontrolle für KI-Systeme erfordert ein robustes Identitätsmanagement, kontextbewusste Autorisierung und eine Durchsetzung zur Laufzeit nach Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten nur mit Modellen, Daten und Rechenressourcen innerhalb ausdrücklich gewährter Zugriffsbereiche interagieren, wobei eine kontinuierliche Überprüfung und Auditierung möglich ist.

---

## C5.1 Identitätsverwaltung & Authentifizierung

Richten Sie kryptografisch gesicherte Identitäten für alle Entitäten ein, mit Multi-Faktor-Authentifizierung für privilegierte Operationen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.1.1 | Stellen Sie sicher, dass alle menschlichen Nutzer und Dienstprinzipale über einen zentralisierten unternehmensweiten Identitätsanbieter (IdP) mittels der OIDC/SAML-Protokolle mit eindeutigen Identitäts-zu-Token-Zuordnungen (keine gemeinsamen Konten oder Anmeldeinformationen) authentifiziert werden. |   1   |  D/V  |
| 5.1.2 | Stellen Sie sicher, dass hochriskante Operationen (Modelldeployment, Gewichteexport, Zugriff auf Trainingsdaten, Änderungen der Produktionskonfiguration) eine Multi-Faktor-Authentifizierung oder eine Step-up-Authentifizierung mit Sitzungsnachvalidierung erfordern.                                    |   1   |  D/V  |
| 5.1.3 | Vergewissern Sie sich, dass neue Verantwortliche eine Identitätsüberprüfung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugriff auf das Produktionssystem erhalten.                                                                                     |   2   |   D   |
| 5.1.4 | Überprüfen Sie, ob Zugriffskontrollen vierteljährlich durchgeführt werden, einschließlich automatischer Erkennung ruhender Konten, Durchsetzung der Anmeldedatenrotation und De-Provisionierungs-Workflows.                                                                                                 |   2   |   V   |
| 5.1.5 | Überprüfen Sie, dass föderierte KI-Agenten sich über signierte JWT-Assertionen authentifizieren, die eine maximale Lebensdauer von 24 Stunden haben und einen kryptografischen Herkunftsnachweis enthalten.                                                                                                 |   3   |  D/V  |

---

## C5.2 Ressourcenautorisierung & Prinzip der geringsten Rechte

Implementieren Sie feinkörnige Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Prüfpfaden.

|   #   | Beschreibung                                                                                                                                                                                                                                                | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.2.1 | Stellen Sie sicher, dass jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Recheninstanzen) rollenbasierte Zugriffskontrollen mit expliziten Erlaubnislisten und Standard-Ablehnungsrichtlinien durchsetzt.          |   1   |  D/V  |
| 5.2.2 | Stellen Sie sicher, dass das Prinzip der geringsten Privilegien standardmäßig bei Servicekonten durchgesetzt wird, beginnend mit nur Lesezugriff und dass eine dokumentierte geschäftliche Rechtfertigung für Schreibzugriff erforderlich ist.              |   1   |  D/V  |
| 5.2.3 | Stellen Sie sicher, dass alle Änderungen der Zugriffskontrolle mit genehmigten Änderungsanfragen verknüpft und unveränderlich protokolliert werden, einschließlich Zeitstempeln, Identitäten der Akteure, Ressourcenkennungen und Berechtigungsdifferenzen. |   1   |   V   |
| 5.2.4 | Verifizieren Sie, dass Datenklassifizierungskennzeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Embeddings, Prompt-Caches, Modellausgaben) mit konsistenter Richtliniendurchsetzung übertragen werden.       |   2   |   D   |
| 5.2.5 | Überprüfen Sie, ob unbefugte Zugriffsversuche und Ereignisse zur Rechteerweiterung Echtzeitbenachrichtigungen mit kontextbezogenen Metadaten innerhalb von 5 Minuten an SIEM-Systeme auslösen.                                                              |   2   |  D/V  |

---

## C5.3 Dynamische Richtlinienbewertung

Setzen Sie attributbasierte Zugriffskontrollsysteme (ABAC) für kontextbewusste Autorisierungsentscheidungen mit Prüfungsfunktionen ein.

|   #   | Beschreibung                                                                                                                                                                                                                                                | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.3.1 | Überprüfen Sie, dass Autorisierungsentscheidungen an eine dedizierte Richtlinien-Engine (OPA, Cedar oder gleichwertig) ausgelagert werden, die über authentifizierte APIs mit kryptografischem Integritätsschutz zugänglich ist.                            |   1   |  D/V  |
| 5.3.2 | Stellen Sie sicher, dass Richtlinien dynamische Attribute zur Laufzeit bewerten, einschließlich der Benutzerfreigabestufe, der Sensitivitätsklassifizierung der Ressource, des Anforderungskontexts, der Mandantenisolierung und zeitlicher Beschränkungen. |   1   |  D/V  |
| 5.3.3 | Stellen Sie sicher, dass Richtliniendefinitionen versioniert, von Kollegen überprüft und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in der Produktion eingesetzt werden.                                                     |   2   |   D   |
| 5.3.4 | Überprüfen Sie, ob die Ergebnisse der Richtlinienbewertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übertragen werden.                                                |   2   |   V   |
| 5.3.5 | Stellen Sie sicher, dass die Time-to-Live (TTL)-Werte des Richtlinien-Caches 5 Minuten für Ressourcen mit hoher Sensitivität und 1 Stunde für Standardressourcen mit Cache-Invalidierungsfunktionen nicht überschreiten.                                    |   3   |  D/V  |

---

## C5.4 Sicherheitsdurchsetzung zur Abfragezeit

Implementieren Sie Sicherheitskontrollen auf Datenbankebene mit obligatorischer Filterung und Zeilenebenen-Sicherheitsrichtlinien.

|   #   | Beschreibung                                                                                                                                                                                                                                                   | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.4.1 | Stellen Sie sicher, dass alle Vektor-Datenbank- und SQL-Abfragen obligatorische Sicherheitsfilter (Mandanten-ID, Sensitivitätskennzeichnungen, Benutzerbereich) enthalten, die auf Ebene der Datenbank-Engine durchgesetzt werden und nicht im Anwendungscode. |   1   |  D/V  |
| 5.4.2 | Überprüfen Sie, ob Richtlinien für die Sicherheit auf Zeilenebene (Row-Level Security, RLS) und Maskierung auf Feldebene mit Richtlinienvererbung für alle Vektordatenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.                              |   1   |  D/V  |
| 5.4.3 | Stellen Sie sicher, dass fehlgeschlagene Autorisierungsbewertungen "Confused-Deputy-Angriffe" verhindern, indem Abfragen sofort abgebrochen und explizite Autorisierungsfehlermeldungen zurückgegeben werden, anstatt leere Ergebnismengen zu liefern.         |   2   |   D   |
| 5.4.4 | Stellen Sie sicher, dass die Latenz der Richtlinienauswertung kontinuierlich überwacht wird, mit automatisierten Warnungen für Zeitüberschreitungsbedingungen, die eine Umgehung der Autorisierung ermöglichen könnten.                                        |   2   |   V   |
| 5.4.5 | Stellen Sie sicher, dass Abfrage-Wiederholmechanismen Autorisierungsrichtlinien erneut bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.                                                                 |   3   |  D/V  |

---

## C5.5 Ausgabe-Filterung & Datenschutz zur Verhinderung von Datenverlust

Setzen Sie Nachbearbeitungskontrollen ein, um die unbefugte Offenlegung von Daten in KI-generierten Inhalten zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                                  | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.5.1 | Stellen Sie sicher, dass Mechanismen zur Filterung nach der Inferenz nicht autorisierte personenbezogene Daten (PII), klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anfragende geliefert werden. |   1   |  D/V  |
| 5.5.2 | Stellen Sie sicher, dass Zitate, Referenzen und Quellenangaben in den Modellausgaben anhand der Berechtigungen des Aufrufers überprüft und entfernt werden, wenn ein unbefugter Zugriff festgestellt wird.                                    |   1   |  D/V  |
| 5.5.3 | Überprüfen Sie, dass die Einschränkungen im Ausgabeformat (bereinigte PDFs, Metadaten-entfernte Bilder, genehmigte Dateitypen) entsprechend den Benutzerberechtigungsstufen und Datenklassifikationen durchgesetzt werden.                    |   2   |   D   |
| 5.5.4 | Stellen Sie sicher, dass Redaktionsalgorithmen deterministisch, versionskontrolliert sind und Prüfprotokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.                                                   |   2   |   V   |
| 5.5.5 | Stellen Sie sicher, dass Hochrisiko-Schwärzungsereignisse adaptive Protokolle erzeugen, die kryptografische Hashes des Originalinhalts für die forensische Wiederherstellung ohne Datenexposition enthalten.                                  |   3   |   V   |

---

## C5.6 Multi-Mandanten-Isolation

Gewährleisten Sie kryptografische und logische Isolation zwischen Mandanten in gemeinsamer KI-Infrastruktur.

|   #   | Beschreibung                                                                                                                                                                                                                      | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.6.1 | Stellen Sie sicher, dass Speicherbereiche, Einbettungsspeicher, Cache-Einträge und temporäre Dateien pro Mandant namespacesegregiert sind und bei Löschung eines Mandanten oder Beendigung einer Sitzung sicher bereinigt werden. |   1   |  D/V  |
| 5.6.2 | Stellen Sie sicher, dass jede API-Anfrage eine authentifizierte Mandantenkennung enthält, die kryptografisch im Vergleich zum Sitzungszusammenhang und den Benutzerberechtigungen validiert wird.                                 |   1   |  D/V  |
| 5.6.3 | Überprüfen Sie, ob Netzwerk-Richtlinien Standard-Verweigern-Regeln für die Kommunikation zwischen Mandanten innerhalb von Service-Meshes und Container-Orchestrierungsplattformen implementieren.                                 |   2   |   D   |
| 5.6.4 | Stellen Sie sicher, dass Verschlüsselungsschlüssel für jeden Mandanten einzigartig sind, mit Unterstützung für kundenseitig verwaltete Schlüssel (CMK) und kryptografischer Isolation zwischen den Datenspeichern der Mandanten.  |   3   |   D   |

---

## C5.7 Autonome Agenten-Autorisierung

Steuerung von Berechtigungen für KI-Agenten und autonome Systeme durch scoped Capability-Tokens und kontinuierliche Autorisierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                           | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.7.1 | Stellen Sie sicher, dass autonome Agenten abgegrenzte Berechtigungstoken erhalten, die ausdrücklich die erlaubten Aktionen, zugänglichen Ressourcen, Zeitgrenzen und betrieblichen Einschränkungen auflisten.                                                          |   1   |  D/V  |
| 5.7.2 | Stellen Sie sicher, dass risikoreiche Funktionen (Dateisystemzugriff, Codeausführung, externe API-Aufrufe, Finanztransaktionen) standardmäßig deaktiviert sind und für ihre Aktivierung eine ausdrückliche Genehmigung mit geschäftlicher Begründung erforderlich ist. |   1   |  D/V  |
| 5.7.3 | Stellen Sie sicher, dass Berechtigungstoken an Benutzersitzungen gebunden sind, eine kryptografische Integritätssicherung enthalten und gewährleisten Sie, dass sie nicht offline gespeichert oder wiederverwendet werden können.                                      |   2   |   D   |
| 5.7.4 | Stellen Sie sicher, dass von Agenten initiierte Aktionen einer sekundären Autorisierung durch die ABAC-Richtlinien-Engine mit vollständiger Kontextbewertung und Auditprotokollierung unterzogen werden.                                                               |   2   |   V   |
| 5.7.5 | Überprüfen Sie, dass Agentenfehlerbedingungen und Ausnahmebehandlungen Informationen zum Fähigkeitsumfang enthalten, um die Vorfallanalyse und forensische Untersuchung zu unterstützen.                                                                               |   3   |   V   |

---

## Referenzen

### Standards & Rahmenwerke

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Implementierungsleitfäden

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### KI-spezifische Sicherheit

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

