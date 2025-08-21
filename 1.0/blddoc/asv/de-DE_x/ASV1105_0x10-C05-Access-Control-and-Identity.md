# C5 Zugriffskontrolle & Identität für KI-Komponenten & Benutzer

## Steuerungsziel

Effektive Zugriffskontrolle für KI-Systeme erfordert ein robustes Identitätsmanagement, kontextbewusste Autorisierung und Laufzeiterzwingung nach Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten nur innerhalb explizit gewährter Bereiche mit Modellen, Daten und Rechenressourcen interagieren, wobei kontinuierliche Überprüfungs- und Auditfähigkeiten gewährleistet sind.

---

## C5.1 Identitätsmanagement & Authentifizierung

Errichten Sie kryptographisch gesicherte Identitäten für alle Entitäten mit Multi-Faktor-Authentifizierung für privilegierte Operationen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.1.1 | Stellen Sie sicher, dass alle menschlichen Benutzer und Dienstprinzipale über einen zentralen unternehmensweiten Identitätsanbieter (IdP) mit OIDC/SAML-Protokollen authentifiziert werden, wobei eindeutige Identitäts-zu-Token-Zuordnungen verwendet werden (keine gemeinsamen Konten oder Anmeldedaten). |   1   |  D/V  |
| 5.1.2 | Stellen Sie sicher, dass für risikoreiche Operationen (Modelleinführung, Gewichts-Export, Zugriff auf Trainingsdaten, Änderungen der Produktionskonfiguration) eine Multi-Faktor-Authentifizierung oder eine erweiterte Authentifizierung mit Sitzungsnevalidierung erforderlich ist.                       |   1   |  D/V  |
| 5.1.3 | Stellen Sie sicher, dass neue Berechtigte eine Identitätsprüfung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugriff auf das produktive System erhalten.                                                                                                |   2   |   D   |
| 5.1.4 | Stellen Sie sicher, dass Zugriffskontrollen vierteljährlich durchgeführt werden, einschließlich automatischer Erkennung inaktiver Konten, Durchsetzung der Anmeldeinformationsrotation und De-Provisioning-Workflows.                                                                                       |   2   |   V   |
| 5.1.5 | Verifizieren Sie, dass föderierte KI-Agenten sich über signierte JWT-Assertions authentifizieren, die eine maximale Lebensdauer von 24 Stunden haben und kryptografischen Ursprungsnachweis enthalten.                                                                                                      |   3   |  D/V  |

---

## C5.2 Ressourcenautorisierung & geringste Privilegien

Implementieren Sie fein abgestufte Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Prüfpfaden.

|   #   | Beschreibung                                                                                                                                                                                                                                           | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 5.2.1 | Verifizieren Sie, dass jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Recheninstanzen) rollenbasierte Zugriffskontrollen mit expliziten Zulassungslisten und Standard-Deny-Richtlinien durchsetzt.           |   1   |  D/V  |
| 5.2.2 | Vergewissern Sie sich, dass das Prinzip der minimalen Rechte standardmäßig bei Dienstkonten durchgesetzt wird, beginnend mit Lesezugriffen, und dass eine dokumentierte geschäftliche Begründung für Schreibzugriffe erforderlich ist.                 |   1   |  D/V  |
| 5.2.3 | Überprüfen Sie, ob alle Änderungen der Zugangskontrolle mit genehmigten Änderungsanfragen verknüpft und unveränderlich protokolliert sind, einschließlich Zeitstempeln, Akteursidentitäten, Ressourcenkennungen und Berechtigungsdifferenzen.          |   1   |   V   |
| 5.2.4 | Stellen Sie sicher, dass Datenklassifizierungsbezeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Embeddings, Prompt-Caches, Modellausgaben) mit einheitlicher Richtliniendurchsetzung übertragen werden. |   2   |   D   |
| 5.2.5 | Stellen Sie sicher, dass unautorisierte Zugriffsversuche und Ereignisse zur Eskalation von Berechtigungen innerhalb von 5 Minuten Echtzeitwarnungen mit kontextbezogenen Metadaten an SIEM-Systeme auslösen.                                           |   2   |  D/V  |

---

## C5.3 Dynamische Richtlinienbewertung

Setzen Sie attributbasierte Zugriffskontrollsysteme (ABAC) für kontextbewusste Autorisierungsentscheidungen mit Prüfungsfunktionen ein.

|   #   | Beschreibung                                                                                                                                                                                                                              | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.3.1 | Überprüfen Sie, dass Autorisierungsentscheidungen an eine dedizierte Richtlinien-Engine (OPA, Cedar oder gleichwertig) ausgelagert sind, die über authentifizierte APIs mit kryptografischem Integritätsschutz zugänglich ist.            |   1   |  D/V  |
| 5.3.2 | Stellen Sie sicher, dass Richtlinien dynamische Attribute zur Laufzeit bewerten, einschließlich Benutzerfreigabestufe, Sensitivitätsklassifizierung der Ressource, Anforderungskontext, Mandantenisolation und zeitliche Einschränkungen. |   1   |  D/V  |
| 5.3.3 | Stellen Sie sicher, dass Richtliniendefinitionen versionskontrolliert, von Kollegen überprüft und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in der Produktion bereitgestellt werden.                      |   2   |   D   |
| 5.3.4 | Überprüfen Sie, ob die Ergebnisse der Richtlinienbewertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übermittelt werden.                             |   2   |   V   |
| 5.3.5 | Überprüfen Sie, dass die Time-to-Live (TTL)-Werte des Richtlinien-Caches 5 Minuten für hochsensible Ressourcen und 1 Stunde für Standardressourcen mit Cache-Invalidierungsmöglichkeiten nicht überschreiten.                             |   3   |  D/V  |

---

## C5.4 Sicherheitsdurchsetzung zur Laufzeit der Abfrage

Implementieren Sie Sicherheitskontrollen auf Datenbankebene mit obligatorischer Filterung und zeilenbasierten Sicherheitsrichtlinien.

|   #   | Beschreibung                                                                                                                                                                                                                                                         | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.4.1 | Stellen Sie sicher, dass alle Abfragen zur Vektordatenbank und SQL obligatorische Sicherheitsfilter (Mandanten-ID, Sensitivitätskennzeichnungen, Benutzerbereich) enthalten, die auf der Ebene der Datenbank-Engine durchgesetzt werden und nicht im Anwendungscode. |   1   |  D/V  |
| 5.4.2 | Überprüfen Sie, dass Richtlinien für die Zeilenebenen-Sicherheit (RLS) und Feldmaskierung mit Richtlinienvererbung für alle Vektordatenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.                                                                   |   1   |  D/V  |
| 5.4.3 | Stellen Sie sicher, dass fehlgeschlagene Autorisierungsprüfungen „confused deputy attacks“ verhindern, indem Abfragen sofort abgebrochen werden und explizite Autorisierungsfehlercodes zurückgegeben werden, anstatt leere Ergebnismengen zu liefern.               |   2   |   D   |
| 5.4.4 | Stellen Sie sicher, dass die Latenz bei der Richtlinienbewertung kontinuierlich mit automatisierten Warnungen bei Zeitüberschreitungsbedingungen überwacht wird, die eine Umgehung der Autorisierung ermöglichen könnten.                                            |   2   |   V   |
| 5.4.5 | Stellen Sie sicher, dass Abfrage-Wiederholmechanismen Autorisierungsrichtlinien neu bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.                                                                          |   3   |  D/V  |

---

## C5.5 Ausgabe-Filterung & Datenschutz (Data Loss Prevention)

Setzen Sie Nachbearbeitungskontrollen ein, um eine unbefugte Offenlegung von Daten in KI-generierten Inhalten zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                             | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 5.5.1 | Überprüfen Sie, dass Nachinferenz-Filtermechanismen unautorisierte personenbezogene Daten (PII), klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anforderer geliefert werden. |   1   |  D/V  |
| 5.5.2 | Überprüfen Sie, ob Zitate, Referenzen und Quellenangaben in den Modellausgaben anhand der Berechtigungen des Anrufers validiert werden und entfernen Sie diese, wenn ein unbefugter Zugriff festgestellt wird.           |   1   |  D/V  |
| 5.5.3 | Stellen Sie sicher, dass Beschränkungen für Ausgabeformate (bereinigte PDFs, metadatenfreie Bilder, genehmigte Dateitypen) basierend auf Benutzerberechtigungsstufen und Datenklassifizierungen durchgesetzt werden.     |   2   |   D   |
| 5.5.4 | Stellen Sie sicher, dass Redaktionsalgorithmen deterministisch, versionskontrolliert sind und Prüfprotokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.                              |   2   |   V   |
| 5.5.5 | Stellen Sie sicher, dass Hochrisiko-Schwärzungsereignisse adaptive Protokolle erzeugen, die kryptographische Hashes des Originalinhalts für die forensische Wiederherstellung ohne Datenexposition enthalten.            |   3   |   V   |

---

## C5.6 Mehrmandanten-Isolierung

Sichern Sie die kryptografische und logische Isolation zwischen Mandanten in gemeinsam genutzter KI-Infrastruktur.

|   #   | Beschreibung                                                                                                                                                                                                          | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.6.1 | Überprüfen Sie, dass Arbeitsspeicherbereiche, Einbettungsspeicher, Cache-Einträge und temporäre Dateien pro Mandant namespace-getrennt sind und bei Mandantenlöschung oder Sitzungsbeendigung sicher gelöscht werden. |   1   |  D/V  |
| 5.6.2 | Stellen Sie sicher, dass jede API-Anfrage eine authentifizierte Mandantenkennung enthält, die kryptografisch gegen den Sitzungs-Kontext und die Benutzerberechtigungen validiert wird.                                |   1   |  D/V  |
| 5.6.3 | Überprüfen Sie, ob Netzwerk-Richtlinien Standard-Deny-Regeln für die Kommunikation zwischen verschiedenen Mandanten innerhalb von Service Meshes und Container-Orchestrierungsplattformen umsetzen.                   |   2   |   D   |
| 5.6.4 | Überprüfen Sie, dass Verschlüsselungsschlüssel pro Mandant eindeutig sind, mit Unterstützung für vom Kunden verwaltete Schlüssel (CMK) und kryptografischer Isolierung zwischen den Datenspeichern der Mandanten.     |   3   |   D   |

---

## C5.7 Autonome Agenten-Autorisierung

Steuerung der Berechtigungen für KI-Agenten und autonome Systeme durch abgegrenzte Fähigkeitstoken und kontinuierliche Autorisierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                           | Ebene | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.7.1 | Verifizieren Sie, dass autonome Agenten Scoped Capability Tokens erhalten, die ausdrücklich die erlaubten Aktionen, zugänglichen Ressourcen, Zeitgrenzen und betrieblichen Beschränkungen auflisten.                                                                   |   1   |  D/V  |
| 5.7.2 | Stellen Sie sicher, dass Hochrisikofunktionen (Dateisystemzugriff, Codeausführung, externe API-Aufrufe, finanzielle Transaktionen) standardmäßig deaktiviert sind und zur Aktivierung eine ausdrückliche Autorisierung mit geschäftlicher Begründung erforderlich ist. |   1   |  D/V  |
| 5.7.3 | Stellen Sie sicher, dass Berechtigungstoken an Benutzersitzungen gebunden sind, eine kryptografische Integritätssicherung enthalten und gewährleisten Sie, dass sie nicht offline gespeichert oder wiederverwendet werden können.                                      |   2   |   D   |
| 5.7.4 | Stellen Sie sicher, dass agenteninitiierte Aktionen eine sekundäre Autorisierung durch die ABAC-Richtlinien-Engine mit vollständiger Kontextbewertung und Audit-Protokollierung durchlaufen.                                                                           |   2   |   V   |
| 5.7.5 | Überprüfen Sie, ob Agentenfehlerbedingungen und Ausnahmebehandlungen Informationen zum Fähigkeitsumfang enthalten, um die Vorfallanalyse und forensische Untersuchung zu unterstützen.                                                                                 |   3   |   V   |

---

## Literaturverzeichnis

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

