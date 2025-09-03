# C5 Zugriffskontrolle und Identität für KI-Komponenten und Benutzer

## Kontrollziel

Wirksame Zugriffskontrolle für KI-Systeme erfordert robuste Identitätsverwaltung, kontextbasierte Autorisierung und Laufzeitsdurchsetzung nach den Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten ausschließlich mit Modellen, Daten und Rechenressourcen innerhalb ausdrücklich gewährter Berechtigungen interagieren, mit kontinuierlicher Verifikation und Auditierbarkeit.

---

## C5.1 Identitätsmanagement & Authentifizierung

Stellen Sie kryptographisch gestützte Identitäten für alle Entitäten bereit, die privilegierte Operationen mit Multi-Faktor-Authentifizierung erfordern.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                          | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.1.1 | Vergewissern Sie sich, dass alle menschlichen Benutzer und Serviceprinzipale sich über einen zentralen unternehmensweiten Identitätsanbieter (IdP) authentifizieren, der OIDC/SAML-Protokolle verwendet, mit eindeutigen Identität-zu-Token-Zuordnungen (keine gemeinsam genutzten Konten oder Anmeldeinformationen). |   1   |  D/V  |
| 5.1.2 | Stellen Sie sicher, dass risikoreiche Operationen (Modellbereitstellung, Gewichtsexport, Zugriff auf Trainingsdaten, Änderungen an der Produktionskonfiguration) eine Mehrfaktor-Authentifizierung oder Step-Up-Authentifizierung mit erneuter Sitzungsvalidierung erfordern.                                         |   1   |  D/V  |
| 5.1.3 | Stellen Sie sicher, dass neue Identitäten eine Identitätsfeststellung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugriff auf das Produktionssystem erhalten.                                                                                                     |   2   |   D   |
| 5.1.4 | Stellen Sie sicher, dass Zugriffsüberprüfungen vierteljährlich durchgeführt werden, mit automatisierter Erkennung inaktiver Konten, Durchsetzung der Rotation von Anmeldeinformationen und Deprovisioning-Workflows.                                                                                                  |   2   |   V   |
| 5.1.5 | Stellen Sie sicher, dass föderierte KI-Agenten sich durch signierte JWT-Aussagen authentifizieren, die eine maximale Lebensdauer von 24 Stunden haben und einen kryptografischen Herkunftsnachweis enthalten.                                                                                                         |   3   |  D/V  |

---

## C5.2 Ressourcenautorisierung und Prinzip der geringsten Privilegien

Implementieren Sie feingranulare Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Audit-Trails.

|   #   | Beschreibung                                                                                                                                                                                                                                              | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.2.1 | Überprüfen Sie, ob jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Compute-Instanzen) rollenbasierte Zugriffskontrollen mit expliziten Allow-Listen und Default-Deny-Richtlinien durchsetzt.                     |   1   |  D/V  |
| 5.2.2 | Vergewissern Sie sich, dass die Prinzipien der geringsten Privilegien standardmäßig durchgesetzt werden, wobei Dienstkonten mit standardmäßigem Lesezugriff beginnen und für Schreibzugriff eine dokumentierte geschäftliche Begründung erforderlich ist. |   1   |  D/V  |
| 5.2.3 | Stellen Sie sicher, dass alle Zugriffskontrolländerungen mit genehmigten Änderungsanträgen verknüpft sind und unveränderlich mit Zeitstempeln, Identitäten der Akteure, Ressourcenkennungen und Berechtigungsänderungen protokolliert werden.             |   1   |   V   |
| 5.2.4 | Stellen Sie sicher, dass Datenklassifikationskennzeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Einbettungen, Promptspeicher, Modellausgaben) mit konsistenter Richtliniendurchsetzung übertragen werden. |   2   |   D   |
| 5.2.5 | Stellen Sie sicher, dass unbefugte Zugriffsversuche und Ereignisse der Privilegieneskalation Echtzeitwarnungen mit kontextbezogenen Metadaten auslösen, die innerhalb von 5 Minuten an SIEM-Systeme übermittelt werden.                                   |   2   |  D/V  |

---

## C5.3 Dynamische Richtlinienbewertung

ABAC-Engines für kontextabhängige Autorisierungsentscheidungen mit Audit-Funktionen bereitstellen.

|   #   | Beschreibung                                                                                                                                                                                                                                                | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.3.1 | Vergewissern Sie sich, dass Autorisierungsentscheidungen an eine dedizierte Policy-Engine (OPA, Cedar oder Äquivalent) externalisiert werden, die über authentifizierte APIs erreichbar ist und kryptographischen Integritätsschutz bietet.                 |   1   |  D/V  |
| 5.3.2 | Stellen Sie sicher, dass Richtlinien dynamische Attribute zur Laufzeit auswerten, einschließlich der Freigabestufe des Benutzers, der Vertraulichkeitseinstufung der Ressource, des Anfragekontexts, der Mandantenisolierung und zeitlicher Beschränkungen. |   1   |  D/V  |
| 5.3.3 | Stellen Sie sicher, dass Richtliniendefinitionen versionskontrolliert, Peer-Review unterzogen und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in die Produktion überführt werden.                                             |   2   |   D   |
| 5.3.4 | Vergewissern Sie sich, dass die Ergebnisse der Richtlinienauswertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übertragen werden.                                      |   2   |   V   |
| 5.3.5 | Überprüfen Sie, dass die Werte des Richtlinien-Cache-Time-to-Live (TTL) 5 Minuten für Ressourcen mit hoher Sensitivität und 1 Stunde für Standardressourcen mit Cache-Invalidierungsfunktionen nicht überschreiten.                                         |   3   |  D/V  |

---

## C5.4 Abfragezeit-Sicherheitsdurchsetzung

Sicherheitskontrollen auf Datenbankebene mit obligatorischer Filterung und Sicherheitsrichtlinien auf Zeilenebene implementieren.

|   #   | Beschreibung                                                                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 5.4.1 | Vergewissern Sie sich, dass alle Abfragen in Vektor-Datenbanken und SQL-Abfragen obligatorische Sicherheitsfilter enthalten (Mandant-ID, Sensitivitätskennzeichnungen, Benutzerbereich), die auf der Ebene der Datenbank-Engine durchgesetzt werden, nicht im Anwendungscode.  |   1   |  D/V  |
| 5.4.2 | Verifizieren Sie, dass Zeilenbasierte Sicherheit (RLS)-Richtlinien und Maskierung auf Feldebene mit Richtlinienvererbung für alle Vektordatenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.                                                                       |   1   |  D/V  |
| 5.4.3 | Stellen Sie sicher, dass fehlgeschlagene Autorisierungsprüfungen verhindern, dass Angriffe durch den verwirrten Beauftragten entstehen, indem Abfragen sofort abgebrochen und explizite Autorisierungsfehlercodes zurückgegeben werden, statt leere Ergebnismengen zu liefern. |   2   |   D   |
| 5.4.4 | Stellen Sie sicher, dass die Latenz der Policy-Auswertung kontinuierlich überwacht wird, mit automatisierten Warnmeldungen bei Timeout-Bedingungen, die eine Autorisierungsumgehung ermöglichen könnten.                                                                       |   2   |   V   |
| 5.4.5 | Überprüfen Sie, ob die Abfrage-Wiederholungsmechanismen die Autorisierungsrichtlinien erneut bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.                                                                           |   3   |  D/V  |

---

## C5.5 Ausgabefilterung & Datenverlustprävention

Implementieren Sie Nachbearbeitungskontrollen, um eine unbefugte Offenlegung von Daten in KI-generierten Inhalten zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                                         | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.5.1 | Vergewissern Sie sich, dass Filtermechanismen nach der Inferenz unbefugte persönlich identifizierbare Informationen (PII), klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anforderer übermittelt werden. |   1   |  D/V  |
| 5.5.2 | Stellen Sie sicher, dass Zitate, Referenzen und Quellenangaben in Modellausgaben gegen die Berechtigungen des Aufrufers validiert werden und entfernt werden, falls unautorisierter Zugriff festgestellt wird.                                       |   1   |  D/V  |
| 5.5.3 | Verifizieren Sie, dass Ausgabeformatbeschränkungen (bereinigte PDFs, Bilder ohne Metadaten, genehmigte Dateitypen) basierend auf den Berechtigungsstufen der Benutzer und den Datenklassifikationen durchgesetzt werden.                             |   2   |   D   |
| 5.5.4 | Stellen Sie sicher, dass Schwärzungsalgorithmen deterministisch sind, versionskontrolliert arbeiten und Audit-Protokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.                                              |   2   |   V   |
| 5.5.5 | Vergewissern Sie sich, dass hochriskante Schwärzungsereignisse adaptive Protokolle erzeugen, die kryptographische Hashwerte des ursprünglichen Inhalts enthalten, zur forensischen Wiederherstellung ohne Offenlegung der Daten.                     |   3   |   V   |

---

## C5.6 Mehrmandanten-Isolation

Sicherstellen kryptographischer und logischer Isolation zwischen Mandanten in einer geteilten KI-Infrastruktur.

|   #   | Beschreibung                                                                                                                                                                                                              | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.6.1 | Stellen Sie sicher, dass Speicherbereiche, Embedding-Speicher, Cache-Einträge und temporäre Dateien mandantenspezifisch isoliert sind und bei Löschung des Mandanten oder Beendigung der Sitzung sicher bereinigt werden. |   1   |  D/V  |
| 5.6.2 | Stellen Sie sicher, dass jede API-Anfrage eine authentifizierte Mandanten-ID enthält, die kryptografisch gegen den Sitzungskontext und die Benutzerberechtigungen validiert wird.                                         |   1   |  D/V  |
| 5.6.3 | Überprüfen Sie, ob Netzwerkrichtlinien Default-Deny-Regeln für mandantenübergreifende Kommunikation innerhalb von Service-Meshes und Container-Orchestrierungsplattformen implementieren.                                 |   2   |   D   |
| 5.6.4 | Stellen Sie sicher, dass pro Mandant eindeutige Verschlüsselungsschlüssel vorhanden sind, CMK-Unterstützung gegeben ist und zwischen den Datenspeichern der Mandanten eine kryptografische Isolation besteht.             |   3   |   D   |

---

## C5.7 Autorisierung autonomer Agenten

Kontrollieren Sie Berechtigungen für KI-Agenten und autonome Systeme durch kontextspezifische Berechtigungs-Tokens und kontinuierliche Autorisierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.7.1 | Stellen Sie sicher, dass autonome Agenten eingeschränkte Berechtigungstokens erhalten, die explizit die zulässigen Aktionen, zugänglichen Ressourcen, zeitliche Grenzen und betriebliche Einschränkungen auflisten.                                                                            |   1   |  D/V  |
| 5.7.2 | Stellen Sie sicher, dass Hochrisikofunktionen (Dateisystemzugriff, Codeausführung, Aufrufe externer APIs, finanzielle Transaktionen) standardmäßig deaktiviert sind und für deren Aktivierung explizite Genehmigungen erforderlich sind, die durch geschäftliche Begründungen gestützt werden. |   1   |  D/V  |
| 5.7.3 | Stellen Sie sicher, dass Berechtigungstoken an Benutzersitzungen gebunden sind, kryptografischen Integritätsschutz bieten und weder gespeichert noch in Offline-Szenarien wiederverwendet werden können.                                                                                       |   2   |   D   |
| 5.7.4 | Stellen Sie sicher, dass die vom Agenten initiierten Aktionen einer sekundären Autorisierung durch die ABAC-Policy-Engine mit vollständiger Kontextauswertung und Audit-Protokollierung unterzogen werden.                                                                                     |   2   |   V   |
| 5.7.5 | Stellen Sie sicher, dass die Fehlerzustände des Agenten und die Ausnahmebehandlung Informationen zum Umfang der Fähigkeiten enthalten, um die Vorfallanalyse und die forensische Untersuchung zu unterstützen.                                                                                 |   3   |   V   |

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

