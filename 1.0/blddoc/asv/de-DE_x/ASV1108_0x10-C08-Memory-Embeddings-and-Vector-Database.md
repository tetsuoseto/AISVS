# C8-Speicher, Einbettungen & Vektor-Datenbanksicherheit

## Kontrollziel

Embeddings und Vektorspeicher fungieren als das „aktive Gedächtnis“ moderner KI-Systeme, indem sie kontinuierlich vom Benutzer bereitgestellte Daten aufnehmen und diese über Retrieval-Augmented Generation (RAG) in die Kontextverarbeitung der Modelle zurückführen. Wenn diese Gedächtnisfunktion ungezügelt bleibt, können personenbezogene Daten (PII) durchsickern, Einwilligungen verletzt oder durch Inversion der ursprüngliche Text rekonstruiert werden. Ziel dieser Kontrollfamilie ist es, Gedächtnispipelines und Vektordatenbanken so abzusichern, dass der Zugriff nach dem Prinzip der minimalen Berechtigung erfolgt, Embeddings datenschutzkonform sind, gespeicherte Vektoren ein Ablaufdatum haben oder auf Anfrage widerrufen werden können und das pro Benutzer gespeicherte Gedächtnis nicht die Eingaben oder Ausgaben anderer Benutzer beeinträchtigt.

---

## C8.1 Zugriffskontrollen auf Speicher- und RAG-Indizes

Durchsetzen von fein abgestuften Zugriffskontrollen für jede Vektorensammlung.

|   #   | Beschreibung                                                                                                                                                                                  | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.1.1 | Überprüfen Sie, ob Zugriffssteuerungsregeln auf Zeilen-/Namespace-Ebene Einfüge-, Lösch- und Abfrageoperationen pro Mandant, Sammlung oder Dokumenten-Tag einschränken.                       |   1   |  D/V  |
| 8.1.2 | Stellen Sie sicher, dass API-Schlüssel oder JWTs eingeschränkte Berechtigungen (z. B. Sammlungs-IDs, Aktionsverben) tragen und mindestens vierteljährlich rotiert werden.                     |   1   |  D/V  |
| 8.1.3 | Überprüfen Sie, dass Versuche zur Eskalation von Privilegien (z. B. Ähnlichkeitsabfragen über Namespace-Grenzen hinweg) innerhalb von 5 Minuten erkannt und an ein SIEM protokolliert werden. |   2   |  D/V  |
| 8.1.4 | Überprüfen Sie, ob die Vektor-Datenbank Protokolle zu Subjekt-Identifier, Operation, Vektor-ID/-Namespace, Ähnlichkeitsschwelle und Ergebnisanzahl führt.                                     |   2   |  D/V  |
| 8.1.5 | Stellen Sie sicher, dass Zugriffsentscheidungen auf Umgehungsmängel geprüft werden, wann immer Engines aktualisiert oder Index-Sharding-Regeln geändert werden.                               |   3   |   V   |

---

## C8.2 Einbettungssanierung & Validierung

Vor der Vektorisierung Text auf personenbezogene Daten (PII) vorab prüfen, diese schwärzen oder pseudonymisieren und optional die Einbettungen nachverarbeiten, um verbleibende Signale zu entfernen.

|   #   | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.2.1 | Stellen Sie sicher, dass PII und regulierte Daten durch automatisierte Klassifikatoren erkannt und vor der Einbettung maskiert, tokenisiert oder entfernt werden.                                                           |   1   |  D/V  |
| 8.2.2 | Stellen Sie sicher, dass Einbettungspipelines Eingaben, die ausführbaren Code oder nicht-UTF-8-Artefakte enthalten und den Index vergiften könnten, ablehnen oder isolieren.                                                |   1   |   D   |
| 8.2.3 | Verifizieren Sie, dass eine lokale oder metrische Differential-Privacy-Sanitisierung auf Satz-Embeddings angewendet wird, deren Abstand zu einem bekannten PII-Token unterhalb eines konfigurierbaren Schwellenwerts liegt. |   2   |  D/V  |
| 8.2.4 | Stellen Sie sicher, dass die Wirksamkeit der Bereinigung (z. B. Rückruf der PII-Entfernung, semantische Abweichung) mindestens halbjährlich anhand von Benchmark-Korpora validiert wird.                                    |   2   |   V   |
| 8.2.5 | Überprüfen Sie, ob die Sanitisierungskonfigurationen versioniert sind und Änderungen einer Peer-Review unterzogen werden.                                                                                                   |   3   |  D/V  |

---

## C8.3 Speicherablauf, Widerruf und Löschung

Die DSGVO "Recht auf Vergessenwerden" und ähnliche Gesetze erfordern eine zeitnahe Löschung; Vektor-Speicher müssen daher TTLs, endgültige Löschungen und Tombstoning unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

|   #   | Beschreibung                                                                                                                                                                                                | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.3.1 | Überprüfen Sie, dass jeder Vektor- und Metadaten-Datensatz eine TTL oder ein explizites Aufbewahrungslabel trägt, das von automatisierten Bereinigungsaufgaben beachtet wird.                               |   1   |  D/V  |
| 8.3.2 | Überprüfen Sie, dass benutzerinitiierte Löschanfragen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen löschen.                                                             |   1   |  D/V  |
| 8.3.3 | Überprüfen Sie, ob logische Löschungen von einer kryptographischen Vernichtung der Speicherblöcke gefolgt werden, wenn die Hardware dies unterstützt, oder durch die Zerstörung der Schlüssel im Key-Vault. |   2   |   D   |
| 8.3.4 | Stellen Sie sicher, dass abgelaufene Vektoren innerhalb von < 500 ms nach Ablauf aus den Ergebnissen der nächsten-Nachbar-Suche ausgeschlossen werden.                                                      |   3   |  D/V  |

---

## C8.4 Verhinderung von Einbettungsumkehr und -leckage

Aktuelle Verteidigungen – Rauschüberlagerung, Projektionsnetzwerke, Privacy-Neuron-Perturbation und Anwendungsschichtverschlüsselung – können die Token-Ebenen-Inversionsraten auf unter 5 % senken.

|   #   | Beschreibung                                                                                                                                                                                           | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.4.1 | Stellen Sie sicher, dass ein formelles Bedrohungsmodell, das Inversions-, Mitgliedschafts- und Attribut-Informationsangriffe abdeckt, existiert und jährlich überprüft wird.                           |   1   |   V   |
| 8.4.2 | Stellen Sie sicher, dass die Verschlüsselung auf Anwendungsebene oder durchsuchbare Verschlüsselung Vektoren vor direktem Zugriff durch Infrastrukturadministratoren oder Cloud-Mitarbeiter schützt.   |   2   |  D/V  |
| 8.4.3 | Überprüfen Sie, dass die Verteidigungsparameter (ε für DP, Rausch-σ, Projektionsrang k) ein Gleichgewicht zwischen Datenschutz ≥ 99 % Token-Schutz und Nutzen ≤ 3 % Genauigkeitsverlust gewährleisten. |   3   |   V   |
| 8.4.4 | Stellen Sie sicher, dass Inversionsresilienzmetriken Teil der Freigabetore für Modellaktualisierungen sind, wobei Regressionsbudgets definiert sind.                                                   |   3   |  D/V  |

---

## C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Cross-Tenant-Lecks bleiben ein hohes Risiko für RAG: Unsachgemäß gefilterte Ähnlichkeitsabfragen können private Dokumente eines anderen Kunden offenlegen.

|   #   | Beschreibung                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.5.1 | Stellen Sie sicher, dass jede Abrageabfrage vor der Übergabe an den LLM-Prompt nach Mandanten-/Benutzer-ID nachgefiltert wird.                                                                                                 |   1   |  D/V  |
| 8.5.2 | Überprüfen Sie, ob Sammlungsnamen oder Namespaced-IDs für jeden Benutzer oder Mandanten gesalzen sind, damit Vektoren über verschiedene Bereiche hinweg nicht kollidieren können.                                              |   1   |   D   |
| 8.5.3 | Stellen Sie sicher, dass Ähnlichkeitsergebnisse, die über einem konfigurierbaren Distanzschwellenwert liegen, aber außerhalb des Gültigkeitsbereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen. |   2   |  D/V  |
| 8.5.4 | Stellen Sie sicher, dass Multi-Tenant-Stresstests adversarielle Anfragen simulieren, die versuchen, Dokumente außerhalb des zulässigen Bereichs abzurufen, und zeigen Sie eine vollständige Vermeidung von Datenleckagen.      |   2   |   V   |
| 8.5.5 | Stellen Sie sicher, dass Verschlüsselungsschlüssel pro Mandant getrennt sind, um kryptografische Isolation zu gewährleisten, selbst wenn der physische Speicher gemeinsam genutzt wird.                                        |   3   |  D/V  |

---

## C8.6 Erweiterte Sicherheit von Speichersystemen

Sicherheitskontrollen für anspruchsvolle Speicherarchitekturen einschließlich episodischem, semantischem und Arbeitsgedächtnis mit spezifischen Anforderungen an Isolierung und Validierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.6.1 | Stellen Sie sicher, dass verschiedene Speichertypen (episodisch, semantisch, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jeden Speichertyp aufweisen. |   1   |  D/V  |
| 8.6.2 | Stellen Sie sicher, dass Speicherfestigungsprozesse eine Sicherheitsvalidierung beinhalten, um die Einschleusung schädlicher Erinnerungen durch Inhaltsbereinigung, Quellenverifizierung und Integritätsprüfungen vor dem Speichern zu verhindern.                             |   2   |  D/V  |
| 8.6.3 | Stellen Sie sicher, dass Speicherabfrageanfragen validiert und bereinigt werden, um die Extraktion unautorisierter Informationen durch Analyse von Abfragemustern, Durchsetzung der Zugriffskontrolle und Filterung der Ergebnisse zu verhindern.                              |   2   |  D/V  |
| 8.6.4 | Verifizieren Sie, dass Speichervergessensmechanismen sensible Informationen sicher löschen und dabei kryptografische Löschungsgarantien durch Schlüssellöschung, Mehrfachüberschreibung oder hardwarebasierte sichere Löschung mit Verifikationszertifikaten gewährleisten.    |   3   |  D/V  |
| 8.6.5 | Überprüfen Sie, dass die Integrität des Speichersystems kontinuierlich auf unautorisierte Änderungen oder Beschädigungen überwacht wird, durch Prüfsummen, Auditprotokolle und automatisierte Alarme, wenn sich der Speicherinhalt außerhalb der normalen Abläufe ändert.      |   3   |  D/V  |

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

