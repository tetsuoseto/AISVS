# C8 Speicher, Embeddings & Vektordatenbanksicherheit

## Kontrollziel

Embeddings und Vektorspeicher fungieren als das „lebendige Gedächtnis“ zeitgenössischer KI-Systeme, indem sie kontinuierlich vom Benutzer bereitgestellte Daten aufnehmen und diese über Retrieval-Augmented Generation (RAG) wieder in Modellkontexte einbringen. Wenn dieses Gedächtnis unbeaufsichtigt bleibt, kann es personenbezogene Daten (PII) preisgeben, gegen Einwilligungen verstoßen oder umgekehrt genutzt werden, um den Originaltext zu rekonstruieren. Ziel dieser Kontrollfamilie ist es, Memory-Pipelines und Vektordatenbanken so zu härten, dass der Zugriff nach dem Prinzip der geringsten Privilegien gewährt wird, Embeddings datenschutzfreundlich sind, gespeicherte Vektoren ablaufen oder auf Anforderung widerrufen werden können und das Gedächtnis eines Nutzers niemals die Eingaben oder Ausgaben eines anderen Nutzers beeinträchtigt.

---

## C8.1 Zugriffskontrollen auf Speicher- und RAG-Indizes

Durchsetzung feinkörniger Zugriffskontrollen für jede Vektorensammlung.

|   #   | Beschreibung                                                                                                                                                                                           | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 8.1.1 | Überprüfen Sie, ob Zugriffssteuerungsregeln auf Zeilen-/Namensraumebene Einfüge-, Lösch- und Abfrageoperationen pro Mandant, Sammlung oder Dokumenten-Tag einschränken.                                |   1    |  D/V  |
| 8.1.2 | Überprüfen Sie, dass API-Schlüssel oder JWTs bereichsspezifische Claims enthalten (z. B. Sammlungs-IDs, Aktionsverben) und mindestens vierteljährlich rotiert werden.                                  |   1    |  D/V  |
| 8.1.3 | Stellen Sie sicher, dass Versuche zur Eskalation von Berechtigungen (z. B. Ähnlichkeitsabfragen über Namespace-Grenzen hinweg) innerhalb von 5 Minuten erkannt und in einem SIEM protokolliert werden. |   2    |  D/V  |
| 8.1.4 | Überprüfen Sie, ob die Vektor-Datenbank das Protokoll mit folgenden Angaben führt: Subjekt-Identifier, Operation, Vektor-ID/Namensraum, Ähnlichkeitsgrenzwert und Ergebnisanzahl.                      |   2    |  D/V  |
| 8.1.5 | Stellen Sie sicher, dass Zugriffsentscheidungen auf Umgehungsmängel getestet werden, wann immer Engines aktualisiert oder Index-Sharding-Regeln geändert werden.                                       |   3    |   V   |

---

## C8.2 Einbettungsbereinigung und Validierung

Vor der Vektorisierung Text auf PII (personenbezogene Daten) vorab prüfen, schwärzen oder pseudonymisieren und optional die Einbettungen nachverarbeiten, um verbleibende Signale zu entfernen.

|   #   | Beschreibung                                                                                                                                                                                                        | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.2.1 | Stellen Sie sicher, dass personenbezogene Daten (PII) und regulierte Daten durch automatisierte Klassifizierer erkannt und vor dem Embedding maskiert, tokenisiert oder entfernt werden.                            |   1    |  D/V  |
| 8.2.2 | Stellen Sie sicher, dass Embedding-Pipelines Eingaben, die ausführbaren Code oder nicht-UTF-8-Artefakte enthalten und den Index vergiften könnten, ablehnen oder in Quarantäne stellen.                             |   1    |   D   |
| 8.2.3 | Überprüfen Sie, ob auf Satz-Einbettungen, deren Abstand zu einem bekannten PII-Token unter einem konfigurierbaren Schwellenwert liegt, eine lokale oder metrische Differential-Privacy-Sanitierung angewendet wird. |   2    |  D/V  |
| 8.2.4 | Vergewissern Sie sich, dass die Wirksamkeit der Bereinigung (z. B. Rückruf bei der PII-Radikalisierung, semantische Abweichung) mindestens halbjährlich anhand von Benchmark-Korpora validiert wird.                |   2    |   V   |
| 8.2.5 | Überprüfen Sie, ob die Sanitierungskonfigurationen versioniert werden und Änderungen einer Peer-Review unterzogen werden.                                                                                           |   3    |  D/V  |

---

## C8.3 Speicherablauf, Widerruf & Löschung

Die DSGVO „Recht auf Vergessenwerden“ und ähnliche Gesetze erfordern eine zeitnahe Löschung; Vektorspeicher müssen daher TTLs, harte Löschungen und Tombstoning unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

|   #   | Beschreibung                                                                                                                                                                                               | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.3.1 | Stellen Sie sicher, dass jeder Vektor- und Metadatensatz eine TTL oder ein explizites Aufbewahrungsetikett trägt, das von automatisierten Bereinigungsaufgaben beachtet wird.                              |   1    |  D/V  |
| 8.3.2 | Überprüfen Sie, ob benutzerinitiierte Löschanfragen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen löschen.                                                              |   1    |  D/V  |
| 8.3.3 | Überprüfen Sie, dass logische Löschungen durch kryptografisches Zerstören der Speicherblöcke gefolgt werden, wenn die Hardware dies unterstützt, oder durch die Zerstörung des Schlüssel-Tresorschlüssels. |   2    |   D   |
| 8.3.4 | Überprüfen Sie, dass abgelaufene Vektoren innerhalb von < 500 ms nach dem Ablauf bei der Suche nach den nächsten Nachbarn ausgeschlossen werden.                                                           |   3    |  D/V  |

---

## C8.4 Verhinderung von Embedding-Inversion und Datenleckage

Neuere Abwehrmaßnahmen—Rauschüberlagerung, Projektionsnetzwerke, Störung von Datenschutz-Neuronen und Verschlüsselung auf Anwendungsebene—können die Inversionsrate auf Token-Ebene auf unter 5 % senken.

|   #   | Beschreibung                                                                                                                                                                                       | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.4.1 | Stellen Sie sicher, dass ein formelles Bedrohungsmodell, das Inversions-, Mitgliedschafts- und Attributinferenzangriffe abdeckt, existiert und jährlich überprüft wird.                            |   1    |   V   |
| 8.4.2 | Stellen Sie sicher, dass Verschlüsselung auf Anwendungsebene oder durchsuchbare Verschlüsselung Vektoren vor direkten Zugriffen durch Infrastrukturadministratoren oder Cloud-Mitarbeiter schützt. |   2    |  D/V  |
| 8.4.3 | Überprüfen Sie, ob die Abwehrparameter (ε für DP, Rauschσ, Projektionsrang k) ein Gleichgewicht zwischen Datenschutz ≥ 99 % Token-Schutz und Nutzbarkeit ≤ 3 % Genauigkeitsverlust gewährleisten.  |   3    |   V   |
| 8.4.4 | Stellen Sie sicher, dass Inversionsresistenzmetriken Teil der Freigabetore für Modellaktualisierungen sind und dabei Regressionsbudgets definiert werden.                                          |   3    |  D/V  |

---

## C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Cross-Tenant-Leckagen bleiben ein großes Risiko bei RAG: unsachgemäß gefilterte Ähnlichkeitsabfragen können private Dokumente eines anderen Kunden sichtbar machen.

|   #   | Beschreibung                                                                                                                                                                                                                 | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.5.1 | Überprüfen Sie, dass jede Abfrage zur Datenabruf vor der Übergabe an das LLM-Prompt anhand der Mandanten-/Benutzer-ID nachgefiltert wird.                                                                                    |   1    |  D/V  |
| 8.5.2 | Stellen Sie sicher, dass Sammlungsnamen oder Namespaced-IDs pro Benutzer oder Mandant gesalzen sind, damit Vektoren über verschiedene Bereiche hinweg nicht kollidieren können.                                              |   1    |   D   |
| 8.5.3 | Stellen Sie sicher, dass Ähnlichkeitsergebnisse oberhalb eines konfigurierbaren Entfernungsgrenzwerts, die jedoch außerhalb des Anwendungsbereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen. |   2    |  D/V  |
| 8.5.4 | Überprüfen Sie, ob Multi-Tenant-Stresstests adversarielle Abfragen simulieren, die versuchen, Dokumente außerhalb des Geltungsbereichs abzurufen, und dabei keine Datenlecks aufweisen.                                      |   2    |   V   |
| 8.5.5 | Stellen Sie sicher, dass Verschlüsselungsschlüssel pro Mandant getrennt sind, um kryptografische Isolation zu gewährleisten, selbst wenn der physische Speicher gemeinsam genutzt wird.                                      |   3    |  D/V  |

---

## C8.6 Erweiterte Sicherheit von Speichersystemen

Sicherheitskontrollen für komplexe Speicherarchitekturen einschließlich episodischem, semantischem und Arbeitsgedächtnis mit spezifischen Anforderungen an Isolation und Validierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                   | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.6.1 | Überprüfen Sie, dass verschiedene Speichertypen (episodisch, semantisch, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jeden Speichertyp haben.                                         |   1    |  D/V  |
| 8.6.2 | Stellen Sie sicher, dass die Speicher-Konsolidierungsprozesse eine Sicherheitsvalidierung beinhalten, um das Einspeisen bösartiger Erinnerungen durch Inhaltsbereinigung, Quellverifizierung und Integritätsprüfungen vor der Speicherung zu verhindern.                                                       |   2    |  D/V  |
| 8.6.3 | Stellen Sie sicher, dass Speicherabrufanfragen validiert und bereinigt werden, um die Extraktion unautorisierter Informationen durch Analyse des Abfragemusters, Durchsetzung der Zugriffskontrolle und Filterung der Ergebnisse zu verhindern.                                                                |   2    |  D/V  |
| 8.6.4 | Verifizieren Sie, dass Mechanismen zum Vergessen von Speicher sensible Informationen sicher mit kryptografischen Löschungsgarantien löschen, indem Sie Schlüssel-Löschung, mehrfache Überschreibung oder hardwarebasierte sichere Löschung mit Verifikationszertifikaten verwenden.                            |   3    |  D/V  |
| 8.6.5 | Stellen Sie sicher, dass die Integrität des Speichersystems kontinuierlich auf unautorisierte Änderungen oder Beschädigungen überwacht wird, indem Prüfsummen, Prüfprotokolle und automatische Warnmeldungen verwendet werden, wenn sich der Speicherinhalt außerhalb der normalen Betriebsbedingungen ändert. |   3    |  D/V  |

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

