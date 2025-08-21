# C5 Zugriffskontrolle & Identität für KI-Komponenten & Nutzer

## Kontrollziel

Effektive Zugriffskontrolle für KI-Systeme erfordert ein robustes Identitätsmanagement, kontextabhängige Autorisierung und eine Laufzeitdurchsetzung nach Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten nur innerhalb ausdrücklich genehmigter Bereiche mit Modellen, Daten und Rechenressourcen interagieren, wobei eine kontinuierliche Überprüfung und Auditfähigkeit gewährleistet ist.

---

## C5.1 Identitätsmanagement & Authentifizierung

Erstellen Sie kryptografisch gesicherte Identitäten für alle Einheiten mit Multi-Faktor-Authentifizierung für privilegierte Operationen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                               | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.1.1 | Stellen Sie sicher, dass alle menschlichen Benutzer und Dienstprinzipale sich über einen zentralen unternehmensweiten Identitätsanbieter (IdP) mithilfe von OIDC-/SAML-Protokollen authentifizieren, wobei eindeutige Identitäts-zu-Token-Zuordnungen verwendet werden (keine geteilten Konten oder Anmeldeinformationen). |   1   |  D/V  |
| 5.1.2 | Verifizieren Sie, dass risikoreiche Operationen (Modelldeployment, Gewichtsexport, Zugriff auf Trainingsdaten, Änderungen der Produktionskonfiguration) eine Multi-Faktor-Authentifizierung oder eine Step-up-Authentifizierung mit Sitzungsnevalidierung erfordern.                                                       |   1   |  D/V  |
| 5.1.3 | Stellen Sie sicher, dass neue Hauptbenutzer eine Identitätsprüfung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugriff auf das Produktionssystem erhalten.                                                                                                             |   2   |   D   |
| 5.1.4 | Stellen Sie sicher, dass Zugangskontrollen vierteljährlich durchgeführt werden, einschließlich automatischer Erkennung inaktiver Konten, Durchsetzung der Anmeldeinformationsrotation und De-Provisioning-Workflows.                                                                                                       |   2   |   V   |
| 5.1.5 | Stellen Sie sicher, dass föderierte KI-Agenten sich über signierte JWT-Assertions authentifizieren, die eine maximale Lebensdauer von 24 Stunden haben und einen kryptografischen Herkunftsnachweis enthalten.                                                                                                             |   3   |  D/V  |

---

## C5.2 Ressourcenautorisierung & geringste Privilegien

Implementieren Sie fein abgestufte Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Prüfpfaden.

|   #   | Beschreibung                                                                                                                                                                                                                                                     | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.2.1 | Stellen Sie sicher, dass jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Recheninstanzen) rollenbasierte Zugriffskontrollen mit expliziten Allow-Listen und Standard-Deny-Richtlinien durchsetzt.                       |   1   |  D/V  |
| 5.2.2 | Stellen Sie sicher, dass das Prinzip der geringsten Privilegien standardmäßig bei Dienstkonten durchgesetzt wird, beginnend mit schreibgeschützten Berechtigungen, und dass eine dokumentierte geschäftliche Rechtfertigung für Schreibzugriff erforderlich ist. |   1   |  D/V  |
| 5.2.3 | Verifizieren Sie, dass alle Änderungen an der Zugriffskontrolle mit genehmigten Änderungsanforderungen verknüpft sind und unveränderlich mit Zeitstempeln, Identitäten der Akteure, Ressourcenkennungen und Berechtigungsdifferenzen protokolliert werden.       |   1   |   V   |
| 5.2.4 | Stellen Sie sicher, dass Datenklassifizierungskennzeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Embeddings, Prompt-Caches, Modellausgaben) mit konsistenter Richtliniendurchsetzung übertragen werden.          |   2   |   D   |
| 5.2.5 | Stellen Sie sicher, dass unautorisierte Zugriffsversuche und Ereignisse zur Eskalation von Berechtigungen Echtzeitwarnungen mit kontextuellen Metadaten an SIEM-Systeme innerhalb von 5 Minuten auslösen.                                                        |   2   |  D/V  |

---

## C5.3 Dynamische Richtlinienbewertung

Setzen Sie attributbasierte Zugriffssteuerungs- (ABAC-) Engines für kontextbewusste Autorisierungsentscheidungen mit Audit-Funktionalitäten ein.

|   #   | Beschreibung                                                                                                                                                                                                                              | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.3.1 | Stellen Sie sicher, dass Autorisierungsentscheidungen an eine dedizierte Policy-Engine (OPA, Cedar oder gleichwertig) ausgelagert werden, die über authentifizierte APIs mit kryptographischem Integritätsschutz zugänglich ist.          |   1   |  D/V  |
| 5.3.2 | Stellen Sie sicher, dass Richtlinien dynamische Attribute zur Laufzeit bewerten, einschließlich Benutzerfreigabestufe, Sensitivitätsklassifizierung der Ressourcen, Anforderungskontext, Mandantentrennung und zeitliche Einschränkungen. |   1   |  D/V  |
| 5.3.3 | Stellen Sie sicher, dass Richtliniendefinitionen versionskontrolliert, von Kollegen überprüft und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in der Produktion eingesetzt werden.                          |   2   |   D   |
| 5.3.4 | Stellen Sie sicher, dass die Ergebnisse der Richtlinienbewertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übermittelt werden.                       |   2   |   V   |
| 5.3.5 | Überprüfen Sie, dass die Time-to-Live (TTL)-Werte des Richtlinien-Caches für hochsensible Ressourcen 5 Minuten und für Standardressourcen mit Cache-Invalidierungsfunktionen 1 Stunde nicht überschreiten.                                |   3   |  D/V  |

---

## C5.4 Sicherheitsdurchsetzung zur Abfragezeit

Implementieren Sie Sicherheitskontrollen auf Datenbankebene mit verpflichtender Filterung und Zeilenebene-Sicherheitsrichtlinien.

|   #   | Beschreibung                                                                                                                                                                                                                                                      | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.4.1 | Stellen Sie sicher, dass alle Vektordatenbank- und SQL-Abfragen obligatorische Sicherheitsfilter (Mandanten-ID, Sensitivitätskennzeichnungen, Benutzerbereich) enthalten, die auf der Ebene der Datenbank-Engine und nicht im Anwendungscode durchgesetzt werden. |   1   |  D/V  |
| 5.4.2 | Stellen Sie sicher, dass zeilenbasierte Sicherheit (RLS)-Richtlinien und feldbasierte Maskierung mit Richtlinienvererbung für alle Vektor-Datenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.                                                        |   1   |  D/V  |
| 5.4.3 | Stellen Sie sicher, dass fehlgeschlagene Autorisierungsbewertungen "Confused-Deputy-Angriffe" verhindern, indem Abfragen sofort abgebrochen und explizite Autorisierungsfehlercodes zurückgegeben werden, anstatt leere Ergebnismengen zurückzugeben.             |   2   |   D   |
| 5.4.4 | Stellen Sie sicher, dass die Auswertungsverzögerung der Richtlinie kontinuierlich überwacht wird und automatisierte Warnmeldungen für Zeitüberschreitungsbedingungen erfolgen, die eine Umgehung der Autorisierung ermöglichen könnten.                           |   2   |   V   |
| 5.4.5 | Stellen Sie sicher, dass Abfrage-Wiederholungsmechanismen die Autorisierungsrichtlinien erneut bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.                                                            |   3   |  D/V  |

---

## C5.5 Ausgabe-Filterung & Verhinderung von Datenverlust

Setzen Sie Nachbearbeitungskontrollen ein, um eine unbefugte Datenfreigabe in KI-generierten Inhalten zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                  | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.5.1 | Stellen Sie sicher, dass Post-Inferenz-Filtermechanismen unautorisierte personenbezogene Daten (PII), klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anforderer geliefert werden. |   1   |  D/V  |
| 5.5.2 | Überprüfen Sie, ob Zitate, Verweise und Quellenangaben in Modellausgaben anhand der Berechtigungen des Aufrufers validiert werden, und entfernen Sie diese, wenn ein unbefugter Zugriff festgestellt wird.                    |   1   |  D/V  |
| 5.5.3 | Überprüfen Sie, ob die Einschränkungen des Ausgabeformats (sichere PDFs, metadatenfreie Bilder, genehmigte Dateitypen) gemäß den Benutzerberechtigungsstufen und Datenklassifikationen durchgesetzt werden.                   |   2   |   D   |
| 5.5.4 | Stellen Sie sicher, dass Schwärzungsalgorithmen deterministisch, versionskontrolliert sind und Prüfprotokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.                                  |   2   |   V   |
| 5.5.5 | Überprüfen Sie, ob Hochrisiko-Schwarzungen adaptive Protokolle erzeugen, die kryptografische Hashwerte des Originalinhalts für die forensische Wiederherstellung ohne Datenexposition enthalten.                              |   3   |   V   |

---

## C5.6 Mehrmandanten-Isolierung

Sicherstellung kryptografischer und logischer Isolation zwischen Mandanten in gemeinsamer KI-Infrastruktur.

|   #   | Beschreibung                                                                                                                                                                                                                     | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.6.1 | Stellen Sie sicher, dass Speicherbereiche, Einbettungsspeicher, Cache-Einträge und temporäre Dateien pro Mandant namespace-separiert sind und beim Löschen des Mandanten oder bei Beendigung der Sitzung sicher gelöscht werden. |   1   |  D/V  |
| 5.6.2 | Stellen Sie sicher, dass jede API-Anfrage einen authentifizierten Mandantenbezeichner enthält, der kryptografisch gegen den Sitzungs kontext und die Benutzerberechtigungen validiert wird.                                      |   1   |  D/V  |
| 5.6.3 | Überprüfen Sie, ob Netzwerk-Richtlinien Default-Deny-Regeln für die Kommunikation zwischen Mandanten innerhalb von Service-Meshes und Container-Orchestrierungsplattformen implementieren.                                       |   2   |   D   |
| 5.6.4 | Überprüfen Sie, dass Verschlüsselungsschlüssel pro Mandant eindeutig sind, mit Unterstützung für kundengesteuerte Schlüssel (CMK) und kryptographischer Isolation zwischen den Mandantendatenspeichern.                          |   3   |   D   |

---

## C5.7 Autonome Agentenautorisierung

Steuerung von Berechtigungen für KI-Agenten und autonome Systeme durch eingeschränkte Fähigkeits-Token und kontinuierliche Autorisierung.

|   #   | Beschreibung                                                                                                                                                                                                                                               | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.7.1 | Stellen Sie sicher, dass autonome Agenten bereichsspezifische Berechtigungstoken erhalten, die ausdrücklich die erlaubten Aktionen, zugänglichen Ressourcen, zeitlichen Begrenzungen und betrieblichen Einschränkungen auflisten.                          |   1   |  D/V  |
| 5.7.2 | Stellen Sie sicher, dass hochriskante Funktionen (Dateisystemzugriff, Codeausführung, externe API-Aufrufe, Finanztransaktionen) standardmäßig deaktiviert sind und eine explizite Autorisierung zur Aktivierung mit geschäftlichen Begründungen erfordern. |   1   |  D/V  |
| 5.7.3 | Überprüfen Sie, dass Fähigkeitstoken an Benutzersitzungen gebunden sind, eine kryptografische Integritätssicherung beinhalten und stellen Sie sicher, dass sie nicht offline gespeichert oder wiederverwendet werden können.                               |   2   |   D   |
| 5.7.4 | Stellen Sie sicher, dass agenteninitiierte Aktionen einer sekundären Autorisierung durch die ABAC-Richtlinien-Engine mit vollständiger Kontextbewertung und Audit-Protokollierung unterzogen werden.                                                       |   2   |   V   |
| 5.7.5 | Stellen Sie sicher, dass Agentenfehlerbedingungen und Ausnahmebehandlungen Informationen zum Fähigkeitsumfang enthalten, um die Vorfallanalyse und forensische Untersuchung zu unterstützen.                                                               |   3   |   V   |

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

