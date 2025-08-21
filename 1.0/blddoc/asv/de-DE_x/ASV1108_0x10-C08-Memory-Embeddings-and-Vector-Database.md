# C8 Speicher, Einbettungen & Vektordatenbank-Sicherheit

## Kontrollziel

Embeddings und Vektorspeicher fungieren als das „lebendige Gedächtnis“ moderner KI-Systeme, die kontinuierlich von Benutzern bereitgestellte Daten aufnehmen und diese über Retrieval-Augmented Generation (RAG) in Modellkontexte zurückführen. Wenn diese Gedächtnisstrukturen nicht reguliert werden, können sie personenbezogene Daten (PII) preisgeben, Einwilligungen verletzen oder so manipuliert werden, dass der Originaltext rekonstruiert wird. Das Ziel dieser Kontrollfamilie ist es, Gedächtnis-Pipelines und Vektordatenbanken so abzusichern, dass der Zugang nach dem Prinzip der minimalen Rechtevergabe erfolgt, Embeddings datenschutzkonform sind, gespeicherte Vektoren ablaufen oder auf Abruf widerrufen werden können, und das Gedächtnis eines Nutzers niemals die Eingaben oder Ausgaben eines anderen Nutzers beeinträchtigt.

---

## C8.1 Zugriffskontrollen auf Speicher- und RAG-Indizes

Durchsetzung fein abgestufter Zugriffskontrollen für jede Vektorsammlung.

|   #   | Beschreibung                                                                                                                                                                                  | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.1.1 | Überprüfen Sie, ob Zugriffskontrollregeln auf Zeilen-/Namespace-Ebene Einfüge-, Lösch- und Abfrageoperationen pro Mandant, Sammlung oder Dokument-Tag einschränken.                           |   1   |  D/V  |
| 8.1.2 | Stellen Sie sicher, dass API-Schlüssel oder JWTs eingeschränkte Ansprüche enthalten (z. B. Sammlungs-IDs, Aktionsverben) und mindestens vierteljährlich ausgetauscht werden.                  |   1   |  D/V  |
| 8.1.3 | Stellen Sie sicher, dass Versuche zur Eskalation von Rechten (z. B. Ähnlichkeitsabfragen über Namespace-Grenzen hinweg) innerhalb von 5 Minuten erkannt und an ein SIEM protokolliert werden. |   2   |  D/V  |
| 8.1.4 | Überprüfen Sie, dass die Vektor-Datenbank Protokolle mit Subjekt-Kennung, Operation, Vektor-ID/-Namespace, Ähnlichkeitsschwelle und Ergebnisanzahl führt.                                     |   2   |  D/V  |
| 8.1.5 | Stellen Sie sicher, dass Zugriffentscheidungen auf Umgehungsmöglichkeiten geprüft werden, wann immer Engines aktualisiert oder Index-Sharding-Regeln geändert werden.                         |   3   |   V   |

---

## C8.2 Einbettungsbereinigung und Validierung

Überprüfen Sie den Text vor der Vektorisierung auf personenbezogene Daten (PII), schwärzen oder pseudonymisieren Sie diese und bearbeiten Sie die Einbettungen optional nach, um verbleibende Signale zu entfernen.

|   #   | Beschreibung                                                                                                                                                                                                           | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.2.1 | Überprüfen Sie, ob personenbezogene Daten (PII) und regulierte Daten durch automatisierte Klassifikatoren erkannt und vor der Einbettung maskiert, tokenisiert oder entfernt werden.                                   |   1   |  D/V  |
| 8.2.2 | Verifizieren Sie, dass Einbettungspipelines Eingaben, die ausführbaren Code oder Nicht-UTF-8-Artefakte enthalten und den Index vergiften könnten, ablehnen oder in Quarantäne stellen.                                 |   1   |   D   |
| 8.2.3 | Überprüfen Sie, ob auf Satz-Einbettungen, deren Abstand zu einem bekannten PII-Token unter einem konfigurierbaren Schwellenwert liegt, eine lokale oder metrische Differential-Datenschutzbereinigung angewendet wird. |   2   |  D/V  |
| 8.2.4 | Stellen Sie sicher, dass die Wirksamkeit der Bereinigung (z. B. Rückrufquote der PII-Radikalisierung, semantische Abweichung) mindestens halbjährlich anhand von Benchmark-Korpora validiert wird.                     |   2   |   V   |
| 8.2.5 | Stellen Sie sicher, dass Sanitierungskonfigurationen versioniert sind und Änderungen einer Peer-Review unterzogen werden.                                                                                              |   3   |  D/V  |

---

## C8.3 Speicherablauf, Widerruf & Löschung

Die DSGVO-"Recht auf Vergessenwerden" und ähnliche Gesetze erfordern eine rechtzeitige Löschung; Vektor-Speicher müssen daher TTLs, endgültige Löschungen und Tombstoning unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

|   #   | Beschreibung                                                                                                                                                                                                                         | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.3.1 | Stellen Sie sicher, dass jeder Vektor- und Metadaten-Datensatz eine TTL oder ein explizites Aufbewahrungsetikett trägt, das von automatisierten Bereinigungsaufgaben eingehalten wird.                                               |   1   |  D/V  |
| 8.3.2 | Stellen Sie sicher, dass von Benutzern initiierte Löschanforderungen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen löschen.                                                                       |   1   |  D/V  |
| 8.3.3 | Stellen Sie sicher, dass logische Löschvorgänge entweder von einer kryptografischen Löschung der Speicherblöcke begleitet werden, falls die Hardware dies unterstützt, oder durch die Zerstörung des Schlüssels im Schlüssel-Tresor. |   2   |   D   |
| 8.3.4 | Stellen Sie sicher, dass abgelaufene Vektoren innerhalb von < 500 ms nach Ablauf in den Ergebnissen der nächsten-Nachbar-Suche ausgeschlossen werden.                                                                                |   3   |  D/V  |

---

## C8.4 Verhinderung von Einbettungsumkehr und Datenleckage

Aktuelle Abwehrmethoden—Rauschüberlagerung, Projektionsnetzwerke, Störung von Privatsphäre-Neuronen und Verschlüsselung auf Anwendungsschicht—können die Inversionsraten auf Token-Ebene unter 5 % senken.

|   #   | Beschreibung                                                                                                                                                                                              | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.4.1 | Stellen Sie sicher, dass ein formelles Bedrohungsmodell existiert, das Umkehrungs-, Mitgliedschafts- und Attributinferenzangriffe abdeckt und jährlich überprüft wird.                                    |   1   |   V   |
| 8.4.2 | Stellen Sie sicher, dass die Verschlüsselung auf Anwendungsebene oder die durchsuchbare Verschlüsselung Vektoren vor direktem Zugriff durch Infrastruktur-Administratoren oder Cloud-Mitarbeiter schützt. |   2   |  D/V  |
| 8.4.3 | Überprüfen Sie, ob die Abwehrparameter (ε für DP, Rauschpegel σ, Projektionsrang k) ein Gleichgewicht zwischen Datenschutz ≥ 99 % Token-Schutz und Nutzbarkeit ≤ 3 % Genauigkeitsverlust gewährleisten.   |   3   |   V   |
| 8.4.4 | Stellen Sie sicher, dass Metriken zur Inversionsresistenz Teil der Freigabekriterien für Modellaktualisierungen sind, wobei Regressionsbudgets definiert sind.                                            |   3   |  D/V  |

---

## C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Cross-Tenant-Lecks bleiben ein großes Risiko bei RAG: Unsachgemäß gefilterte Ähnlichkeitsabfragen können private Dokumente eines anderen Kunden offenlegen.

|   #   | Beschreibung                                                                                                                                                                                                        | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.5.1 | Stellen Sie sicher, dass jede Abfrage zur Datenabfrage nach der Mandanten-/Benutzer-ID gefiltert wird, bevor sie an das LLM-Prompt weitergegeben wird.                                                              |   1   |  D/V  |
| 8.5.2 | Stellen Sie sicher, dass Sammlungsnamen oder mit einem Namespace versehene IDs pro Benutzer oder Mandant gesalzen sind, damit Vektoren über verschiedene Bereiche hinweg nicht kollidieren können.                  |   1   |   D   |
| 8.5.3 | Überprüfen Sie, dass Ähnlichkeitsergebnisse, die über einem konfigurierbaren Distanzschwellenwert liegen, jedoch außerhalb des Bereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen.   |   2   |  D/V  |
| 8.5.4 | Stellen Sie sicher, dass Multi-Tenant-Stresstests adversariale Anfragen simulieren, die versuchen, auf nicht autorisierte Dokumente zuzugreifen, und zeigen Sie eine vollständige Vermeidung von Informationslecks. |   2   |   V   |
| 8.5.5 | Stellen Sie sicher, dass die Verschlüsselungsschlüssel pro Mandant getrennt sind, um eine kryptografische Isolation zu gewährleisten, selbst wenn der physische Speicher gemeinsam genutzt wird.                    |   3   |  D/V  |

---

## C8.6 Fortgeschrittene Speichersystem-Sicherheit

Sicherheitskontrollen für anspruchsvolle Speicherarchitekturen, einschließlich episodischem, semantischem und Arbeitsgedächtnis mit spezifischen Anforderungen an Isolierung und Validierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                         | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.6.1 | Überprüfen Sie, dass die verschiedenen Speichertypen (episodisch, semantisch, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jeden Speichertyp aufweisen.                      |   1   |  D/V  |
| 8.6.2 | Stellen Sie sicher, dass Speicherkonsolidierungsprozesse eine Sicherheitsvalidierung umfassen, um die Einspeisung bösartiger Erinnerungen durch Inhaltsbereinigung, Quellenverifizierung und Integritätsprüfungen vor der Speicherung zu verhindern.                                                 |   2   |  D/V  |
| 8.6.3 | Stellen Sie sicher, dass Speicherabrufanfragen validiert und bereinigt werden, um die Extraktion unautorisierter Informationen durch Analyse von Abfragemustern, Durchsetzung von Zugriffskontrollen und Ergebnisfilterung zu verhindern.                                                            |   2   |  D/V  |
| 8.6.4 | Überprüfen Sie, dass Mechanismen zum Vergessen von Speicher sensible Informationen sicher mit kryptografischen Löschgarantien löschen, indem Sie Schlüssel löschen, mehrfach überschreiben oder hardwarebasierte sichere Löschung mit Verifikationszertifikaten verwenden.                           |   3   |  D/V  |
| 8.6.5 | Stellen Sie sicher, dass die Integrität des Speichersystems kontinuierlich auf unbefugte Änderungen oder Beschädigungen überwacht wird, indem Prüfsummen, Audit-Protokolle und automatische Benachrichtigungen verwendet werden, wenn sich der Speicherinhalt außerhalb der normalen Abläufe ändert. |   3   |  D/V  |

---

## Referenzen

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

