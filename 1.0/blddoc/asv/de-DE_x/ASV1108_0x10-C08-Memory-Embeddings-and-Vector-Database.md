# C8 Memory, Einbettungen & Vektordatenbank-Sicherheit

## Kontrollziel

Einbettungen und Vektor-Speicher fungieren als das 'Live-Memory' zeitgenössischer KI-Systeme, die kontinuierlich nutzerbereitgestellte Daten akzeptieren und sie über Retrieval-Augmented Generation (RAG) wieder in Modellkontexte einbringen. Wird dieses Gedächtnis unbeaufsichtigt gelassen, kann es personenbezogene Daten (PII) offengelegen, Zustimmung verletzen oder so manipuliert werden, dass der ursprüngliche Text rekonstruiert werden kann. Das Ziel dieser Kontrollfamilie besteht darin, Speicher-Pipelines und Vektor-Datenbanken zu härten, damit der Zugriff dem Prinzip der geringsten Privilegien entspricht, die Einbettungen datenschutzfreundlich sind, gespeicherte Vektoren verfallen oder auf Abruf widerrufen werden können, und benutzerbezogener Speicher niemals die Eingaben oder Generierungen eines anderen Benutzers beeinflusst.

---

## C8.1 Zugriffskontrollen auf Speicher- und RAG-Indizes

Durchsetzen Sie feingranulierte Zugriffskontrollen für jede Vektorsammlung.

|   #   | Beschreibung                                                                                                                                                                                    | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.1.1 | Stellen Sie sicher, dass Zugriffskontrollregeln auf Zeilen- und Namensraum-Ebene Einfüge-, Lösch- und Abfragevorgänge pro Mandant, Sammlung oder Dokument-Tag einschränken.                     |   1   |  D/V  |
| 8.1.2 | Stellen Sie sicher, dass API-Schlüssel oder JWTs bereichsspezifische Ansprüche tragen (z. B. Sammlungs-IDs, Aktionsverben) und dass sie mindestens vierteljährlich rotiert werden.              |   1   |  D/V  |
| 8.1.3 | Stellen Sie sicher, dass Privilegieneskalationsversuche (z. B. Namensräume übergreifende Ähnlichkeitsabfragen) innerhalb von 5 Minuten erkannt und in ein SIEM protokolliert werden.            |   2   |  D/V  |
| 8.1.4 | Verifizieren Sie, dass die Auditprotokolle der Vektor-Datenbank Folgendes protokollieren: Subjekt-Identifikator, Vorgang, Vektor-ID/Namensraum, Ähnlichkeitsschwelle und Anzahl der Ergebnisse. |   2   |  D/V  |
| 8.1.5 | Stellen Sie sicher, dass Zugriffsentscheidungen auf Umgehungsschwachstellen getestet werden, wann immer Engines aktualisiert werden oder sich Index-Sharding-Regeln ändern.                     |   3   |   V   |

---

## C8.2 Einbettungs-Sanitierung und Validierung

Text vor der Vektorisierung auf PII prüfen, personenbezogene Daten schwärzen oder pseudonymisieren, und optional Embeddings nachbearbeiten, um verbleibende Signale zu entfernen.

|   #   | Beschreibung                                                                                                                                                                                                              | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.2.1 | Stellen Sie sicher, dass PII (personenbezogene Daten) und regulierte Daten durch automatisierte Klassifikatoren erkannt werden und vor der Einbettung maskiert, tokenisiert oder verworfen werden.                        |   1   |  D/V  |
| 8.2.2 | Stellen Sie sicher, dass Embedding-Pipelines Eingaben ablehnen oder in Quarantäne stellen, die ausführbaren Code oder nicht-UTF-8-Artefakte enthalten, die den Index schädigen könnten.                                   |   1   |   D   |
| 8.2.3 | Überprüfen Sie, ob eine lokale oder metrische Differential-Privacy-Sanitisierung auf Satz-Einbettungen angewendet wird, deren Abstand zu jedem bekannten PII-Token unterhalb eines konfigurierbaren Schwellenwerts liegt. |   2   |  D/V  |
| 8.2.4 | Stellen Sie sicher, dass die Wirksamkeit der Sanitisierung (z. B. Recall der PII-Schwärzung, semantische Drift) mindestens halbjährlich gegen Benchmark-Korpora validiert wird.                                           |   2   |   V   |
| 8.2.5 | Vergewissern Sie sich, dass Sanitisierungskonfigurationen versionskontrolliert sind und Änderungen einem Peer-Review unterzogen werden.                                                                                   |   3   |  D/V  |

---

## C8.3 Speicherablauf, Widerruf und Löschung

DSGVO "Recht auf Vergessenwerden" und ähnliche Gesetze verlangen eine rechtzeitige Löschung; Vektorspeicher müssen daher TTLs, unwiderrufliche Löschungen und Löschmarkierungen unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

|   #   | Beschreibung                                                                                                                                                                                          | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.3.1 | Überprüfen Sie, dass jeder Vektor- und Metadaten-Eintrag eine TTL oder eine explizite Aufbewahrungskennzeichnung trägt, die von automatisierten Bereinigungsaufgaben berücksichtigt wird.             |   1   |  D/V  |
| 8.3.2 | Stellen Sie sicher, dass durch benutzerinitiierte Löschanfragen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen gelöscht werden.                                     |   1   |  D/V  |
| 8.3.3 | Überprüfen Sie, ob logische Löschvorgänge von kryptografischer Vernichtung der Speicherblöcke gefolgt werden, sofern die Hardware dies unterstützt, oder durch Zerstörung der Schlüssel im Key Vault. |   2   |   D   |
| 8.3.4 | Verifizieren Sie, dass abgelaufene Vektoren innerhalb von < 500 ms nach dem Ablauf aus den Ergebnissen der nächstgelegenen Nachbarsuche ausgeschlossen werden.                                        |   3   |  D/V  |

---

## C8.4 Verhinderung von Einbettungsinversion und Datenleck

Neuere Abwehrmaßnahmen—Rauschüberlagerung, Projektionsnetzwerke, Privatsphäre-Neuronen-Perturbation und Anwendungsschicht-Verschlüsselung—können Token-Ebene-Inversionsraten unter 5% senken.

|   #   | Beschreibung                                                                                                                                                                                                                       | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.4.1 | Stellen Sie sicher, dass ein formales Bedrohungsmodell existiert, das Inversion, Mitgliedschafts-Inferenzangriffe und Attribut-Inferenzangriffe abdeckt, und dass es jährlich überprüft wird.                                      |   1   |   V   |
| 8.4.2 | Stellen Sie sicher, dass die Anwendungsschicht-Verschlüsselung oder die durchsuchbare Verschlüsselung Vektoren vor direktem Lesen durch Infrastruktur-Administratoren oder Cloud-Mitarbeiter schützt.                              |   2   |  D/V  |
| 8.4.3 | Verifizieren Sie, dass Schutzparameter (ε für DP, Rauschen σ, Projektionsrang k) eine Balance zwischen Privatsphäre und Nutzwert herstellen, bei der Privatsphäre ≥ 99 % Token-Schutz und Nutzwert ≤ 3 % Genauigkeitsverlust gilt. |   3   |   V   |
| 8.4.4 | Vergewissern Sie sich, dass Metriken zur Resilienz gegenüber Inversionen Teil der Freigabe-Gates für Modellaktualisierungen sind, wobei Regressionsbudgets definiert sind.                                                         |   3   |  D/V  |

---

## C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Mandantenübergreifendes Datenleck bleibt eines der größten RAG-Risiken: Unangemessen gefilterte Ähnlichkeitsabfragen können die privaten Dokumente eines anderen Kunden offenlegen.

|   #   | Beschreibung                                                                                                                                                                                                                         | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.5.1 | Stellen Sie sicher, dass jede Abrufabfrage nachträglich durch die Mandanten-/Benutzer-ID gefiltert wird, bevor sie an die LLM-Eingabeaufforderung übergeben wird.                                                                    |   1   |  D/V  |
| 8.5.2 | Stellen Sie sicher, dass Sammlungsnamen oder Namensraum-IDs pro Benutzer oder Mandant gesalzen werden, damit Vektoren über verschiedene Geltungsbereiche hinweg nicht kollidieren.                                                   |   1   |   D   |
| 8.5.3 | Stellen Sie sicher, dass Ähnlichkeitsergebnisse, die über einen konfigurierbaren Abstandsschwellenwert hinausgehen, aber außerhalb des Gültigkeitsbereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen. |   2   |  D/V  |
| 8.5.4 | Stellen Sie sicher, dass Mehrmandanten-Stresstests feindliche Abfragen simulieren, die darauf abzielen, außerhalb des Geltungsbereichs liegende Dokumente abzurufen, und dass dabei keinerlei Leckage entsteht.                      |   2   |   V   |
| 8.5.5 | Überprüfen Sie, ob Verschlüsselungsschlüssel mandantenweise isoliert sind, um kryptografische Isolation sicherzustellen, auch wenn der physische Speicher geteilt wird.                                                              |   3   |  D/V  |

---

## C8.6 Fortgeschrittene Speichersystem-Sicherheit

Sicherheitsmaßnahmen für anspruchsvolle Speicherarchitekturen, einschließlich episodischem, semantischem und Arbeitsgedächtnis, mit spezifischen Isolations- und Validierungsanforderungen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                      | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.6.1 | Überprüfen Sie, ob verschiedene Speicherarten (episodisches Gedächtnis, semantisches Gedächtnis, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jede Speicherart aufweisen. |   1   |  D/V  |
| 8.6.2 | Stellen Sie sicher, dass Speicher-Konsolidierungsprozesse eine Sicherheitsvalidierung beinhalten, um die Injektion schädlicher Erinnerungen durch Inhaltsbereinigung, Quellenverifizierung und Integritätsprüfungen vor der Speicherung zu verhindern.                                            |   2   |  D/V  |
| 8.6.3 | Stellen Sie sicher, dass Speicherabrufabfragen validiert und bereinigt werden, um zu verhindern, dass unautorisierte Informationen extrahiert werden, durch die Analyse von Abfragemustern, die Durchsetzung von Zugriffskontrollen und die Ergebnisfilterung.                                    |   2   |  D/V  |
| 8.6.4 | Überprüfen Sie, dass Speicherlöschmechanismen sensible Informationen sicher löschen und kryptografische Löschgarantien verwenden, indem sie Schlüssellöschung, Mehrfachüberschreibung oder hardwarebasierte sichere Löschung mit Verifikationszertifikaten einsetzen.                             |   3   |  D/V  |
| 8.6.5 | Stellen Sie sicher, dass die Integrität des Speichersystems kontinuierlich überwacht wird, um unbefugte Modifikationen oder Beschädigungen durch Prüfsummen, Audit-Protokolle und automatisierte Warnmeldungen zu erkennen, wenn sich der Speicherinhalt außerhalb normaler Operationen ändert.   |   3   |  D/V  |

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

